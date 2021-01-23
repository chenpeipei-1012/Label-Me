<template>
    <div class="home">
        <func-list class="func-list"></func-list>
        <display ref="display" class="display"></display>
        <object-list class="object-list"></object-list>
        <Drawer title="文件列表" :draggable="true" v-model="fileItemsShowFlag">
            <CellGroup style="width: fit-content;">
                <template v-for="(item, index) in fileItems">
                    <Cell :title="item.annotation" :selected="item.selected" @click.native="openFile(index)" style="padding: 0 0 0 0;"/>
                </template>
            </CellGroup>
        </Drawer>
    </div>
</template>

<script>
  import FuncList from './children/FuncList'
  import Display from './children/Display'
  import ObjectList from './children/ObjectList'
  export default {
    name: 'Home',
    components: {FuncList, Display, ObjectList},
    data () {
      return {
        fileItemsShowFlag: false,
        fileItemsSelectedIndex: -1,
        fileItems: [{
          directory: '',
          annotation: '',
          image: '',
          x: 0,
          y: 0,
          gender: '',
          age: '',
          upper_wear: '',
          lower_wear: '',
          upper_color: '',
          lower_color: '',
          upper_wear_texture: '',
          bag: '',
          upper_wear_fg: '',
          headwear: '',
          glasses: '',
          umbrella: '',
          cellphone: '',
          orientation: '',
          smoke: '',
          carrying_item: '',
          vehicle: '',
          lower_cut: '',
          upper_cut: '',
          occlusion: '',
          is_human: '',
          scale: 1,
          objects: []
        }]
      }
    },
    methods: {
      showFileItems (fileItems) {
        if (fileItems) {
          this.fileItems = fileItems
        }
        this.fileItemsShowFlag = true
      },
      openFile (index) {
        console.log('index', index)
        this.fileItems.forEach(item => (item.selected = false))
        this.fileItems[index].selected = true
        this.fileItemsSelectedIndex = index
        let fileItem = this.fileItems[index]
        this.$refs.display.loadImgAttr(fileItem)
      },
      getIndex () {
        console.log('当前的打开的是', this.fileItemsSelectedIndex)
        return this.fileItemsSelectedIndex
      }
    }
  }
</script>

<style scoped>
    .home {
        height: 100%;
        margin:0;
        padding:0;
        display: flex;
        flex-direction: row;
    }
    .func-list {
        width: 8%;
        height: 100%;
    }
    .display {
        width: 72%;
        height: 100%;
        background: #dcdee2;
    }
    .object-list {
        width: 20%;
        height: 100%;
        background: aqua;
    }
</style>
