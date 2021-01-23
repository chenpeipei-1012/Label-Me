<template>
    <div class="func-list">
        <func-btn button="primary" icon="ios-folder-open" text="Open Dir"
                  @click.native="openDirectory()"></func-btn>
        <func-btn button="warning" icon="ios-list-box" text="File List"
                  @click.native="showFileItems()"></func-btn>
        <func-btn button="info" icon="md-add" text="Zoom In"
                  @click.native="zoomIn()"></func-btn>
        <func-btn button="info" icon="md-remove" text="Zoom Out"
                  @click.native="zoomOut()"></func-btn>
        <func-btn button="info" icon="md-archive" text="Save"
                  @click.native="saveFileItemObjects()"></func-btn>
        <func-btn button="info" icon="md-arrow-round-forward" text="Next"
                  @click.native="nextimg()"></func-btn>
        <func-btn button="info" icon="md-arrow-back" text="Last"
                  @click.native="lastimg()"></func-btn>
<!--        <func-btn button="info" icon="ios-square-outline" text="Draw Box"></func-btn>-->
    </div>
</template>

<script>
  import FuncBtn from './children/FuncBtn'
  const {dialog} = require('electron').remote
  const fs = require('fs')
  const path = require('path')
  export default {
    name: 'FuncList',
    components: {FuncBtn},
    methods: {
      openDirectory () {
        let ret = dialog.showOpenDialog({
          properties: ['openDirectory']
        })
        if (!ret) {
          this.$Message.info('Not selectBoundingBox directory')
        } else {
          let dir = ret[0]
          if (!fs.existsSync(dir)) {
            this.$Message.error(dir + ' not exist')
          } else if (!fs.statSync(dir).isDirectory()) {
            this.$Message.error(dir + ' is not a directory')
          } else {
            let filenames = fs.readdirSync(dir)
            let annotations = filenames.filter(filename => path.extname(filename) === '.xml')
            let images = filenames.filter(filename => path.extname(filename) === '.jpg' ||
              path.extname(filename) === '.png' || path.extname(filename) === '.jpeg')
            let fileItems = []
            annotations.forEach(value => fileItems.push({
              'annotation': value,
              'image': images.find(name => name.startsWith(path.basename(value, 'xml'))),
              'directory': dir,
              'selected': false,
              'x': 0,
              'y': 0,
              'scale': 1,
              'objects': []
            }))
            this.$parent.showFileItems(fileItems)
          }
        }
      },
      showFileItems () {
        this.$parent.showFileItems()
      },
      zoomIn () {
        this.$parent.$refs.display.zoomIn()
      },
      zoomOut () {
        this.$parent.$refs.display.zoomOut()
      },
      saveFileItemObjects () {
        // t.ok(robot.keyTap('a', 'control') === 1, 'successfully tapped "ctrl+a".')
        this.$parent.$refs.display.saveFileItemObjects()
      },
      lastimg () {
        // this.$parent.$refs.display.saveFileItemObjects()
        let index = this.$parent.getIndex()
        if (index === 0) {
          this.$Message.error('这是第一张图片')
        } else {
          index = index - 1
        }
        this.$parent.openFile(index)
      },
      nextimg () {
        this.$parent.$refs.display.saveFileItemObjects()
        let index = this.$parent.getIndex() + 1
        this.$parent.openFile(index)
      }
    }
  }
</script>

<style scoped>
    .func-list {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
</style>
