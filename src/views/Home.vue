<template>
  <div :class="{drag:dragging}">
    <div class="layout-container">
      <div :class="key" v-for="(item, key) in mainData" :key="key">
        <draggable
          v-bind="dragOptions"
          class="list-group"
          :list="item"
          @end="onEnd"
          @start="onStart"
        >
          <transition-group name="list">
            <div class="list-group-item" v-for="(element, index) in item" :key="index">
              <div class="drag-handle">{{ element.title }}</div>
              <div class="component-box">
                <component :is="element.name"/>
              </div>
            </div>
          </transition-group>
        </draggable>
      </div>
    </div>
  </div>
</template>
<script>
import draggable from "vuedraggable";
import {
  timeline,
  calendar,
  welcome,
  carousel,
  imgs,
  KonList
} from "@/components/DragComponents";
import { constants } from "crypto";

export default {
  components: {
    draggable,
    timeline,
    calendar,
    welcome,
    carousel,
    imgs,
    KonList
  },
  data() {
    return {
      dragging: false,
      componentList: [
        { name: "KonList", title: "追番地址", id: "5" },
        { name: "imgs", title: "五月最强新番", id: "4" },
        { name: "timeline", title: "日程组件", id: "2" },
        { name: "carousel", title: "走马灯组件", id: "1" },
        { name: "calendar", title: "日历组件", id: "3" }
      ],
      layout: {
        left: ["5", "4"],
        right: ["2", "1", "3"]
      },
      mainData: {}
    };
  },
  computed: {
    dragOptions() {
      return {
        animation: 30,
        handle: ".drag-handle",
        group: "description",
        ghostClass: "ghost",
        chosenClass: "sortable",
        forceFallback: true
      };
    }
  },
  mounted() {
      this.getLayout();
  },
  methods: {
    onStart() {
      this.dragging = true;
    },
    onEnd() {
      this.dragging = false;
      this.setLayout();
    },
    getLayout() {
      let myLayout = JSON.parse(window.localStorage.getItem("kon"));
      if (!myLayout || Object.keys(myLayout).length === 0)
        myLayout = this.layout;
      const newLayout = {};
      for (const side in myLayout) {
        newLayout[side] = myLayout[side].map(i => {
          return this.componentList.find(c => c.id === i);
        });
      }
      this.mainData = newLayout;
    },
    setLayout() {
      const res = {};
      for (const side in this.mainData) {
        const item = this.mainData[side].map(i => i.id);
        res[side]=item;
      }
      window.localStorage.setItem("kon", JSON.stringify(res));
    }
  }
};
</script>
<style lang="scss" scoped>
.layout-container {
  height: 100%;
  display: flex;
  .left {
    flex: 1;
    margin-right: 40px;
  }
  .right {
    max-width: 550px;
    width: 550px;
  }
  .list-group-item {
    margin-bottom: 20px;
    border-radius: 6px;
    overflow: hidden;
    background: #fff;
  }
  .component-box {
    padding: 20px;
  }
  .drag-handle {
    cursor: move;
    height: 40px;
    line-height: 40px;
    color: #fff;
    font-weight: 700;
    font-size: 16px;
    padding: 0 20px;
    background: #6cf;
  }
}
.drag {
  .component-box {
    display: none;
  }
}

.list-enter-active {
  transition: all .3s linear;

}
.list-enter,
.list-leave-to {
  opacity: .5;
}

.sortable {
  .component-box {
    display: none;
    height: 0;
  }
}
.list-group {
  > span {
    display: block;
    min-height: 20px;
  }
}

.ghost {
  .drag-handle {
    background: rgb(129, 168, 187);
  }
}
</style>