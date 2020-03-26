<template>
  <div class="container">
    <div class="row custom-row">
      <b-icon class="chevron-up-icon" icon="chevron-up"></b-icon>
      <b-icon class="chevron-down-icon" icon="chevron-down"></b-icon>
      <b-icon class="add-top-icon" icon="plus-circle-fill"></b-icon>
      <b-icon class="trash-icon" icon="trash"></b-icon>
      <b-icon class="settings-icon" icon="gear-fill"></b-icon>
      <b-icon class="add-bottom-icon" icon="plus-circle-fill"></b-icon>
      <b-icon class="plus-icon" @click="addColumn" icon="plus"></b-icon>
      <div class="dynamic-column" v-for="(div, index) in allDiv" v-bind:index="index" v-bind:key="div" v-html="div" ref="mydiv"></div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import { BootstrapVue, BootstrapVueIcons } from "bootstrap-vue";

Vue.use(BootstrapVue);
Vue.use(BootstrapVueIcons);
export default Vue.extend({
  data() {
    return {
      allDiv: []
    };
  },
  methods: {
    addColumn() {
      console.log("column added");
      let newColumn =
        '<div class="resizable" draggable="true">';
      newColumn += '<span class="material-icons drag">drag_indicator</span>';
      newColumn += '<span id="delete" class="material-icons trash" @click="addColumn">delete_outline</span>';
      newColumn += '<span class="material-icons settings">settings</span>';
      // newColumn += '<img class="logo display btn dlt-btn" onClick={this.deleteDiv} id={index} src={logo} />';
      // newColumn += '<img class="btn display" id={index} src={drag} />';
      // newColumn += '<img src={{resize}} class="display text-btn" id={index} onClick={this.input}/>';
      newColumn += '<textarea placeholder="Type Something"></textarea></div>';
      this.allDiv.push(newColumn);
    },
    deleteColumn() {

    },
    resizeCoulumn() {},
    deleteRow() {},
    collapseRow() {},
    expandRow() {}
  }
});
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  text-align: center;
}

.custom-row {
  border: 1px solid #ddd;
  width: 100%;
  height: 300px;
  margin: 10px auto;
  position: relative;
}

.trash-icon {
  position: absolute;
  top: 0;
  right: 0;
  margin: 5px;
}

.settings-icon {
  position: absolute;
  bottom: 0;
  margin: 5px;
}

.plus-icon {
  position: absolute;
  bottom: 0;
  margin: 5px;
  right: 0;
}

.add-top-icon {
  position: absolute;
  z-index: 9999;
  width: 100%;
  top: -9px;
}

.add-bottom-icon {
  position: absolute;
  z-index: 9999;
  width: 100%;
  bottom: -8px;
}

.resizable {
  border: 1px solid #ddd;
  margin: 10px;
  position: relative;
}

.dynamic-column div {
  height: 90%;
}

textarea {
  margin: 30px auto 10px auto;
  height: 80%;
  width: 90%;
  border: none;
  outline: none;
}

span.material-icons.trash {
  right: 0;
  position: absolute;
  margin: 5px;
  font-size: 20px;
}

span.material-icons.settings {
  position: absolute;
  bottom: 0;
  left: 0;
  margin: 5px;
  font-size: 20px;
}

span.material-icons.drag {
  position: absolute;
  top: 0;
  left: 0;
  margin: 5px;
  font-size: 20px;
}
</style>
