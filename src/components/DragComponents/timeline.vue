<template>
  <div class="block">
    <el-timeline>
      <el-timeline-item
        v-for="(activity, index) in activities"
        :key="index"
        :timestamp="activity.timestamp"
      >{{activity.content}}</el-timeline-item>
    </el-timeline>
  </div>
</template>

<script>
export default {
  data() {
    return {
      activities: [
        {
          content: "补番《轻音少女剧场版》",
          timestamp: "2019-05-23"
        },
        {
          content: "补番《轻音少女第二季》",
          timestamp: "2019-05-22"
        },
        {
          content: "补番《轻音少女第一季》",
          timestamp: "2019-05-21"
        }
      ]
    };
  }
};
</script>