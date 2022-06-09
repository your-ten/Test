<template>
  <div class="hello">
    <GridLayout
      :layout.sync="layout"
      :col-num="12"
      :row-height="30"
      :is-draggable="true"
      :is-resizable="true"
      :is-mirrored="false"
      :vertical-compact="true"
      :margin="[10, 10]"
      :use-css-transforms="true"
      @layout-created="layoutCreatedEvent"
      @layout-before-mount="layoutBeforeMountEvent"
      @layout-mounted="layoutMountedEvent"
      @layout-ready="layoutReadyEvent"
      @layout-updated="layoutUpdatedEvent"
    >
      <grid-item v-for="item in layout"
        :x="item.x"
        :y="item.y"
        :w="item.w"
        :h="item.h"
        :i="item.i"
        :key="item.i"
        :maxH="10"
        :max-w="4"
        :isDraggable="true"
        :isResizable="null"
        :static="false"
        @resize="resizeEvent"
        @move="moveEvent"
        @resized="resizedEvent"
        @moved="movedEvent">
        {{item.i}}
      </grid-item>
    </GridLayout>
  </div>
</template>

<script>
  import VueGridLayout from 'vue-grid-layout';
  var testLayout = [
    {"x":0,"y":0,"w":2,"h":2,"i":"0"},
    {"x":2,"y":0,"w":2,"h":4,"i":"1"},
    {"x":4,"y":0,"w":2,"h":5,"i":"2"},
    {"x":6,"y":0,"w":2,"h":3,"i":"3"},
    {"x":8,"y":0,"w":2,"h":3,"i":"4"},
    {"x":10,"y":0,"w":2,"h":3,"i":"5"},
    {"x":0,"y":5,"w":2,"h":5,"i":"6"},
    {"x":2,"y":5,"w":2,"h":5,"i":"7"},
    {"x":4,"y":5,"w":2,"h":5,"i":"8"},
    {"x":6,"y":3,"w":2,"h":4,"i":"9"},
    {"x":8,"y":4,"w":2,"h":4,"i":"10"},
    {"x":10,"y":4,"w":2,"h":4,"i":"11"},
    {"x":0,"y":10,"w":2,"h":5,"i":"12"},
    {"x":2,"y":10,"w":2,"h":5,"i":"13"},
    {"x":4,"y":8,"w":2,"h":4,"i":"14"},
    {"x":6,"y":8,"w":2,"h":4,"i":"15"},
    {"x":8,"y":10,"w":2,"h":5,"i":"16"},
    {"x":10,"y":4,"w":2,"h":2,"i":"17"},
    {"x":0,"y":9,"w":2,"h":3,"i":"18"},
    {"x":2,"y":6,"w":2,"h":2,"i":"19"}
  ];
  export default {
    // 忽略本地修改内容
    props: {
      GridLayout: VueGridLayout.GridLayout,
      GridItem: VueGridLayout.GridItem
    },
    data(){
      return {
        layout: testLayout,
      }
    },
    methods:{
      layoutCreatedEvent: function(newLayout){
        console.log("Created layout: ", newLayout)
      },
      layoutBeforeMountEvent: function(newLayout){
        console.log("beforeMount layout: ", newLayout)
      },
      layoutMountedEvent: function(newLayout){
        console.log("Mounted layout: ", newLayout)
      },
      layoutReadyEvent: function(newLayout){
        console.log("Ready layout: ", newLayout)
      },
      layoutUpdatedEvent: function(newLayout){
        console.log("Updated layout: ", newLayout)
      },

      moveEvent: function(i, newX, newY){
        console.log("MOVE i=" + i + ", X=" + newX + ", Y=" + newY);
      },
      resizeEvent: function(i, newH, newW, newHPx, newWPx){
        console.log("RESIZE i=" + i + ", H=" + newH + ", W=" + newW + ", H(px)=" + newHPx + ", W(px)=" + newWPx);
      },
      movedEvent: function(i, newX, newY){
        console.log("MOVED i=" + i + ", X=" + newX + ", Y=" + newY);
      },
      resizedEvent: function(i, newH, newW, newHPx, newWPx){
        console.log("RESIZED i=" + i + ", H=" + newH + ", W=" + newW + ", H(px)=" + newHPx + ", W(px)=" + newWPx);
      },
    }
  }
</script>

<style scoped>
  .vue-grid-item {
    background: rgba(102, 109, 68, 0.5);
  }
</style>
