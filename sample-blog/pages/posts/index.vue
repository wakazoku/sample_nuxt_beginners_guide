<template>
  <section class="container posts-page">
    <el-card>
      <div slot="header" class="clearfix">
        <span>新着投稿</span>
      </div>
      <el-table :data="showPosts" style="width:100%;" class="table">
        <el-table-column prop="title" label="タイトル"></el-table-column>
        <el-table-column
          prop="user.id"
          label="投稿者"
          width="180"
        ></el-table-column>
        <el-table-column
          prop="created_at"
          label="投稿日時"
          width="240"
        ></el-table-column>
      </el-table>
    </el-card>
  </section>
</template>
<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  computed: {
    showPosts() {
      return [
        {
          id: "001",
          title: "how to develop nuxt.js application",
          body: "body bodybodybodybody body body body body body body body body",
          created_at: "2020/12/03 12:00:00",
          user: {
            id: "wakazoku"
          }
        },
        {
          id: "002",
          title: "development nuxt.js application to heroku",
          body: "body bodybodybodybody body body body body body body body body",
          created_at: "2020/12/03 13:00:00",
          user: {
            id: "wakazoku"
          }
        }
      ];
    }
  }
});
</script>

<style lang="scss" scoped>
.posts-page ::v-deep .el-table__row {
  cursor: pointer !important;
}
</style>
