<template>
  <section class="container posts-page">
    <el-card>
      <div slot="header" class="clearfix">
        <span>新着投稿</span>
      </div>
      <el-table
        :data="showPosts"
        style="width:100%;"
        class="table"
        @row-click="handleClick"
      >
        <el-table-column prop="post.title" label="タイトル"></el-table-column>
        <el-table-column
          prop="post.user.id"
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

<script>
import Vue from "vue";
import moment from "~/plugins/moment";
import { mapGetters } from "vuex";

export default Vue.extend({
  async asyncData({ store }) {
    await store.dispatch("posts/fetchPosts");
  },
  computed: {
    showPosts() {
      return this.posts.map(post => {
        post.created_at = moment(post.created_at).format("YYYY/MM/DD HH:mm:ss");
        return post;
      });
    },
    ...mapGetters("posts", ["posts"])
  },
  methods: {
    handleClick(post) {
      this.$router.push(`/posts/${post.id}`);
    }
  }
});
</script>

<style lang="scss" scoped>
.posts-page ::v-deep .el-table__row {
  cursor: pointer !important;
}
</style>
