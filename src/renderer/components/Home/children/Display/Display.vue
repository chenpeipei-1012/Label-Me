<template>
    <div class="display" :draggable="true"
         @dragstart="dragImageStart($event)" @drag="dragImagePeriod($event)">
        <span class="scale">{{fileItem.scale * 100}}%</span>
        <span class="origin">({{fileItem.x}}, {{fileItem.y}})</span>
        <img :draggable="false" :src="imageUrl" :style="imageStyle" >
          <template v-for="(_, index) in fileItem.objects">
              <bounding-box v-model="fileItem.objects[index]"></bounding-box>
          </template>
        <img id='ghost' src="~@/assets/logo.png" style="visibility: hidden;">
<!--        <Card :model="fileItem" class="card">-->
<!--          <FormItem label="性别">-->
<!--            <RadioGroup v-model="fileItem.gender">-->
<!--              <Radio label="男性">男性</Radio>-->
<!--              <Radio label="女性">女性</Radio>-->
<!--            </RadioGroup>-->
<!--          </FormItem>-->
<!--          <FormItem label="性别">-->
<!--            <RadioGroup v-model="fileItem.gender">-->
<!--              <Radio label="男性">男性</Radio>-->
<!--              <Radio label="女性">女性</Radio>-->
<!--            </RadioGroup>-->
<!--          </FormItem>-->
<!--        </Card>-->

        <Form :model="fileItem" :label-width="80" class="attr">
          <FormItem label="性别">
            <RadioGroup v-model="fileItem.gender">
              <Radio label="男性">男性</Radio>
              <Radio label="女性">女性</Radio>
            </RadioGroup>
          </FormItem>
          <FormItem label="年龄">
            <RadioGroup v-model="fileItem.age">
              <Radio label="幼儿">幼儿</Radio>
              <Radio label="青少年">青少年</Radio>
              <Radio label="青年">青年</Radio>
              <Radio label="中年">中年</Radio>
              <Radio label="老年">老年</Radio>
            </RadioGroup>
          </FormItem>
          <FormItem label="袖子长短">
            <RadioGroup v-model="fileItem.upper_wear">
              <Radio label="长袖">长袖</Radio>
              <Radio label="短袖">短袖</Radio>
            </RadioGroup>
          </FormItem>
          <FormItem label="裤子长短">
            <RadioGroup v-model="fileItem.lower_wear">
              <Radio label="长裤">长裤</Radio>
              <Radio label="短裤">短裤</Radio>
              <Radio label="长裙">长裙</Radio>
              <Radio label="短裙">短裙</Radio>
              <Radio label="不确定">不确定</Radio>
            </RadioGroup>
          </FormItem>
          <FormItem label="上衣颜色">
            <RadioGroup v-model="fileItem.upper_color">
              <Radio label="红">红</Radio>
              <Radio label="橙">橙</Radio>
              <Radio label="黄">黄</Radio>
              <Radio label="绿">绿</Radio>
              <Radio label="蓝">蓝</Radio>
              <Radio label="紫">紫</Radio>
              <Radio label="粉">粉</Radio>
              <Radio label="黑">黑</Radio>
              <Radio label="白">白</Radio>
              <Radio label="灰">灰</Radio>
              <Radio label="棕">棕</Radio>
            </RadioGroup>
          </FormItem>
          <FormItem label="下身颜色">
            <RadioGroup v-model="fileItem.lower_color">
              <Radio label="红">红</Radio>
              <Radio label="橙">橙</Radio>
              <Radio label="黄">黄</Radio>
              <Radio label="绿">绿</Radio>
              <Radio label="蓝">蓝</Radio>
              <Radio label="紫">紫</Radio>
              <Radio label="粉">粉</Radio>
              <Radio label="黑">黑</Radio>
              <Radio label="白">白</Radio>
              <Radio label="灰">灰</Radio>
              <Radio label="棕">棕</Radio>
              <Radio label="棕">棕</Radio>
              <Radio label="不确定">不确定</Radio>
            </RadioGroup>
          </FormItem>
          <FormItem label="上衣">
            <RadioGroup v-model="fileItem.upper_wear_texture">
              <Radio label="纯色">纯色</Radio>
              <Radio label="图案">图案</Radio>
              <Radio label="碎花">碎花</Radio>
              <Radio label="条纹或格子">条纹或格子</Radio>
            </RadioGroup>
          </FormItem>
          <FormItem label="下方截断">
            <RadioGroup v-model="fileItem.lower_cut">
              <Radio label="有下方截断">有</Radio>
              <Radio label="无下方截断">无</Radio>
            </RadioGroup>
          </FormItem>
          <FormItem label="下方截断">
            <RadioGroup v-model="fileItem.lower_cut">
              <Radio label="有下方截断">有</Radio>
              <Radio label="无下方截断">无</Radio>
            </RadioGroup>
          </FormItem>          <FormItem label="下方截断">
            <RadioGroup v-model="fileItem.lower_cut">
              <Radio label="有下方截断">有</Radio>
              <Radio label="无下方截断">无</Radio>
            </RadioGroup>
          </FormItem>          <FormItem label="下方截断">
            <RadioGroup v-model="fileItem.lower_cut">
              <Radio label="有下方截断">有</Radio>
              <Radio label="无下方截断">无</Radio>
            </RadioGroup>
          </FormItem>          <FormItem label="下方截断">
            <RadioGroup v-model="fileItem.lower_cut">
              <Radio label="有下方截断">有</Radio>
              <Radio label="无下方截断">无</Radio>
            </RadioGroup>
          </FormItem>          <FormItem label="下方截断">
            <RadioGroup v-model="fileItem.lower_cut">
              <Radio label="有下方截断">有</Radio>
              <Radio label="无下方截断">无</Radio>
            </RadioGroup>
          </FormItem>          <FormItem label="下方截断">
            <RadioGroup v-model="fileItem.lower_cut">
              <Radio label="有下方截断">有</Radio>
              <Radio label="无下方截断">无</Radio>
            </RadioGroup>
          </FormItem>          <FormItem label="下方截断">
            <RadioGroup v-model="fileItem.lower_cut">
              <Radio label="有下方截断">有</Radio>
              <Radio label="无下方截断">无</Radio>
            </RadioGroup>
          </FormItem>          <FormItem label="下方截断">
            <RadioGroup v-model="fileItem.lower_cut">
              <Radio label="有下方截断">有</Radio>
              <Radio label="无下方截断">无</Radio>
            </RadioGroup>
          </FormItem>          <FormItem label="下方截断">
            <RadioGroup v-model="fileItem.lower_cut">
              <Radio label="有下方截断">有</Radio>
              <Radio label="无下方截断">无</Radio>
            </RadioGroup>
          </FormItem>          <FormItem label="下方截断">
            <RadioGroup v-model="fileItem.lower_cut">
              <Radio label="有下方截断">有</Radio>
              <Radio label="无下方截断">无</Radio>
            </RadioGroup>
          </FormItem>          <FormItem label="下方截断">
            <RadioGroup v-model="fileItem.lower_cut">
              <Radio label="有下方截断">有</Radio>
              <Radio label="无下方截断">无</Radio>
            </RadioGroup>
          </FormItem>          <FormItem label="下方截断">
            <RadioGroup v-model="fileItem.lower_cut">
              <Radio label="有下方截断">有</Radio>
              <Radio label="无下方截断">无</Radio>
            </RadioGroup>
          </FormItem>          <FormItem label="下方截断">
            <RadioGroup v-model="fileItem.lower_cut">
              <Radio label="有下方截断">有</Radio>
              <Radio label="无下方截断">无</Radio>
            </RadioGroup>
          </FormItem>          <FormItem label="下方截断">
            <RadioGroup v-model="fileItem.lower_cut">
              <Radio label="有下方截断">有</Radio>
              <Radio label="无下方截断">无</Radio>
            </RadioGroup>
          </FormItem>          <FormItem label="下方截断">
            <RadioGroup v-model="fileItem.lower_cut">
              <Radio label="有下方截断">有</Radio>
              <Radio label="无下方截断">无</Radio>
            </RadioGroup>
          </FormItem>          <FormItem label="下方截断">
            <RadioGroup v-model="fileItem.lower_cut">
              <Radio label="有下方截断">有</Radio>
              <Radio label="无下方截断">无</Radio>
            </RadioGroup>
          </FormItem>          <FormItem label="下方截断">
            <RadioGroup v-model="fileItem.lower_cut">
              <Radio label="有下方截断">有</Radio>
              <Radio label="无下方截断">无</Radio>
            </RadioGroup>
          </FormItem>          <FormItem label="下方截断">
            <RadioGroup v-model="fileItem.lower_cut">
              <Radio label="有下方截断">有</Radio>
              <Radio label="无下方截断">无</Radio>
            </RadioGroup>
          </FormItem>
          <FormItem label="上方截断">
            <RadioGroup v-model="fileItem.upper_cut">
              <Radio label="有上方截断">有</Radio>
              <Radio label="无上方截断">无</Radio>
            </RadioGroup>
          </FormItem>
        </Form>
    </div>
</template>

<script>
  import BoundingBox from './children/BoundingBox'
  import img from '../../../../assets/1.2.jpg'
  const fs = require('fs')
  const xml2js = require('xml2js')
  const parser = new xml2js.Parser()
  const builder = new xml2js.Builder()
  export default {
    name: 'Display',
    components: { BoundingBox },
    data () {
      return {
        imageUrl: img,
        fileItem: {
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
          objects: [
            {
              originX: 0,
              originY: 0,
              x: 120,
              y: 100,
              width: 60,
              height: 60,
              scale: 1,
              name: 'hello',
              selected: false
            },
            {
              originX: 0,
              originY: 0,
              x: 30,
              y: 50,
              width: 40,
              height: 30,
              scale: 1,
              name: 'world',
              selected: false
            }
          ]
        },
        dragX: 0,
        dragY: 0,
        SCALE_LEVEL: [0.20, 0.40, 0.60, 0.80, 1, 1.20, 1.40, 1.60, 1.8, 2, 3, 4]
      }
    },
    computed: {
      imageStyle () {
        return {
          'position': 'absolute',
          'left': this.fileItem.x + 'px',
          'top': this.fileItem.y + 'px',
          'transform-origin': 'left top',
          '-webkit-transform': 'scale(' + this.fileItem.scale + ')'
        }
      }
    },
    methods: {
      loadImage (fileItem) {
        this.fileItem = fileItem
        this.imageUrl = 'file://' + fileItem.directory + '/' + fileItem.image
        // load annotation box
        const vm = this
        let annotationPath = fileItem.directory + '/' + fileItem.annotation
        fs.readFile(annotationPath, 'utf-8', function (error, data) {
          if (error) {
            vm.$Message.error(error)
            console.log(error)
          } else {
            xml2js.parseString(data, function (error, result) {
              if (error) {
                vm.$Message.error(error)
                console.log(error)
              } else {
                console.log(result)
                console.log(typeof result.annotation.object)
                result.annotation.object.forEach(value => fileItem.objects.push({
                  originX: fileItem.x,
                  originY: fileItem.y,
                  x: Number(value.bndbox[0].xmin[0]),
                  y: Number(value.bndbox[0].ymin[0]),
                  width: Number(value.bndbox[0].xmax[0]) - Number(value.bndbox[0].xmin[0]),
                  height: Number(value.bndbox[0].ymax[0]) - Number(value.bndbox[0].ymin[0]),
                  scale: fileItem.scale,
                  name: value.name[0],
                  selected: false
                }))
              }
            })
          }
        })
      },
      loadImgAttr (fileItem) {
        this.fileItem = fileItem
        this.imageUrl = 'file://' + fileItem.directory + '/' + fileItem.image
        // load annotation
        const vm = this
        let annotationPath = fileItem.directory + '/' + fileItem.annotation
        // fs.writeFile(annotationPath,'')
        fs.readFile(annotationPath, 'utf-8', function (error, data) {
          if (error) {
            vm.$Message.error(error)
            console.log(error)
          } else {
            parser.parseString(data, function (error, result) {
              if (error) {
                vm.$Message.error(error)
                console.log(error)
              } else {
                let arrresult = result.root
                console.log('arrresult : ', arrresult)
                for (var key in arrresult) {
                  console.log(key)
                  console.log(arrresult[key][0]['lbel'][0])
                  switch (key) {
                    case 'gender':
                      fileItem.gender = arrresult[key][0]['lbel'][0]
                      break
                    case 'age':
                      fileItem.age = arrresult[key][0]['lbel'][0]
                      break
                    case 'upper_wear':
                      fileItem.upper_wear = arrresult[key][0]['lbel'][0]
                      break
                    case 'lower_wear':
                      fileItem.lower_wear = arrresult[key][0]['lbel'][0]
                      break
                    case 'upper_color':
                      fileItem.upper_color = arrresult[key][0]['lbel'][0]
                      break
                    case 'lower_color':
                      fileItem.lower_color = arrresult[key][0]['lbel'][0]
                      break
                    case 'upper_wear_texture':
                      fileItem.upper_wear_texture = arrresult[key][0]['lbel'][0]
                      break
                    case 'bag':
                      fileItem.bag = arrresult[key][0]['lbel'][0]
                      break
                    case 'upper_wear_fg':
                      fileItem.upper_wear_fg = arrresult[key][0]['lbel'][0]
                      break
                    case 'headwear':
                      fileItem.headwear = arrresult[key][0]['lbel'][0]
                      break
                    case 'glasses':
                      fileItem.glasses = arrresult[key][0]['lbel'][0]
                      break
                    case 'umbrella':
                      fileItem.umbrella = arrresult[key][0]['lbel'][0]
                      break
                    case 'cellphone':
                      fileItem.cellphone = arrresult[key][0]['lbel'][0]
                      break
                    case 'orientation':
                      fileItem.orientation = arrresult[key][0]['lbel'][0]
                      break
                    case 'smoke':
                      fileItem.smoke = arrresult[key][0]['lbel'][0]
                      break
                    case 'carrying_item':
                      fileItem.carrying_item = arrresult[key][0]['lbel'][0]
                      break
                    case 'vehicle':
                      fileItem.vehicle = arrresult[key][0]['lbel'][0]
                      break
                    case 'upper_cut':
                      fileItem.upper_cut = arrresult[key][0]['lbel'][0]
                      break
                    case 'lower_cut':
                      fileItem.lower_cut = arrresult[key][0]['lbel'][0]
                      break
                    case 'occlusion':
                      fileItem.occlusion = arrresult[key][0]['lbel'][0]
                      break
                    case 'is_human':
                      fileItem.is_human = arrresult[key][0]['lbel'][0]
                      break
                  }
                }
                console.log(fileItem)
              }
            })
          }
        })
      },
      saveFileItemObjects () {
        let fileItem = this.fileItem
        this.imageUrl = 'file://' + fileItem.directory + '/' + fileItem.image
        // load annotation
        const vm = this
        let annotationPath = fileItem.directory + '/' + fileItem.annotation
        console.log('annotationPath', annotationPath)
        fs.readFile(annotationPath, 'utf-8', function (error, data) {
          if (error) {
            vm.$Message.error(error)
            console.log(error)
          } else {
            xml2js.parseString(data, function (error, result) {
              if (error) {
                vm.$Message.error(error)
                console.log(error)
              } else {
                let attresult = result.root
                attresult['gender'][0]['lbel'][0] = fileItem.gender
                attresult['age'][0]['lbel'][0] = fileItem.age
                attresult['upper_wear'][0]['lbel'][0] = fileItem.upper_wear
                attresult['lower_wear'][0]['lbel'][0] = fileItem.lower_wear
                attresult['upper_color'][0]['lbel'][0] = fileItem.upper_color
                attresult['lower_color'][0]['lbel'][0] = fileItem.lower_color
                attresult['upper_wear_texture'][0]['lbel'][0] = fileItem.upper_wear_texture
                attresult['bag'][0]['lbel'][0] = fileItem.bag
                attresult['upper_wear_fg'][0]['lbel'][0] = fileItem.upper_wear_fg
                attresult['headwear'][0]['lbel'][0] = fileItem.headwear
                attresult['glasses'][0]['lbel'][0] = fileItem.glasses
                attresult['umbrella'][0]['lbel'][0] = fileItem.umbrella
                attresult['cellphone'][0]['lbel'][0] = fileItem.cellphone
                attresult['orientation'][0]['lbel'][0] = fileItem.orientation
                attresult['smoke'][0]['lbel'][0] = fileItem.smoke
                attresult['carrying_item'][0]['lbel'][0] = fileItem.carrying_item
                attresult['vehicle'][0]['lbel'][0] = fileItem.vehicle
                attresult['upper_cut'][0]['lbel'][0] = fileItem.upper_cut
                attresult['lower_cut'][0]['lbel'][0] = fileItem.lower_cut
                attresult['occlusion'][0]['lbel'][0] = fileItem.occlusion
                attresult['is_human'][0]['lbel'][0] = fileItem.is_human
                console.log('after attresult+', attresult)
                fs.writeFile(annotationPath, builder.buildObject(attresult), 'utf-8', function (err) {
                  if (err) {
                    return console.log(err)
                  } else {
                    // vm.$Message.success('修改成功')
                    console.log('写入成功')
                  }
                })
              }
            }
            )
          }
        })
      },
      nextimg () {
      },
      unselectAllBoundingBox () {
        this.fileItem.objects.forEach(function (object) {
          object.selected = false
        })
        this.$children.forEach(function (boundingBox) {
          boundingBox.$refs.root.style.zIndex = 1
        })
      },
      dragImageStart (event) {
        // replace drag image with a hidden image
        event.dataTransfer.setDragImage(document.getElementById('ghost'), 0, 0)
        this.dragX = event.x
        this.dragY = event.y
      },
      dragImagePeriod (event) {
        if (event.x === 0 && event.y === 0) return
        let offsetX = event.x - this.dragX
        let offsetY = event.y - this.dragY
        this.fileItem.x += offsetX
        this.fileItem.y += offsetY
        this.fileItem.objects.forEach(function (object) {
          object.originX += offsetX
          object.originY += offsetY
        })
        this.dragX = event.x
        this.dragY = event.y
      },
      zoomIn () {
        const scaleLevel = this.SCALE_LEVEL
        let scaleIndex = scaleLevel.findIndex(value => value === this.fileItem.scale)
        if (scaleIndex < scaleLevel.length - 1) {
          this.fileItem.scale = scaleLevel[scaleIndex + 1]
          this.fileItem.objects.forEach(function (object) {
            object.scale = scaleLevel[scaleIndex + 1]
          })
        } else {
          this.$Message.warning('Max scale level')
        }
      },
      zoomOut () {
        const scaleLevel = this.SCALE_LEVEL
        let scaleIndex = scaleLevel.findIndex(value => value === this.fileItem.scale)
        if (scaleIndex > 0) {
          this.fileItem.scale = scaleLevel[scaleIndex - 1]
          this.fileItem.objects.forEach(function (object) {
            object.scale = scaleLevel[scaleIndex - 1]
          })
        } else {
          this.$Message.warning('Min scale level')
        }
      }
    }
  }
</script>

<style scoped>
    .display {
        position: relative;
        overflow: hidden;
    }
    .scale {
        position: absolute;
        top: 0;
        left: 1vmin;
        font-size: 4vmin;
        color: #ed4014;
        z-index: 1000;
    }
    .origin {
        position: absolute;
        top: 0;
        right: 1vmin;
        font-size: 4vmin;
        color: #ed4014;
        z-index: 1000;
    }
    .card {
        position: absolute;
        top: 0;
        left: 1vmin;
        font-size: 4vmin;
    }

    /*.attr >>> .iview-class{*/
    /*    position: absolute;*/
    /*    top: 40px;*/
    /*    right: 1vmin;*/
    /*    font-size: 4vmin;*/
    /*}*/
</style>
<style>
  .attr {
    position: absolute;
    top: 40px;
    right: 1vmin;
    font-size: 4vmin;
    line-height: 0;
  }
</style>
