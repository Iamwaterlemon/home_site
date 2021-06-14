<template>
  <el-container>
    <el-main>
      <el-row :gutter="10">
        <el-col :span="8" v-for="item in dataSource" :key="item.id">
          <el-button @click="handleClick(item)">
            <el-card :body-style="{ padding: '0px' }" shadow="hover" >
              <img :src="item.imgSrc" class="image">
              <div style="padding: 14px;">
                <strong>{{ item.label }}</strong>
              </div>
<!--              <div class="bottom">-->
<!--                <el-button type="text" class="button"  @click="dialogVisible = true" >详情</el-button>-->
<!--              </div>-->
            </el-card>
          </el-button>
        </el-col>
      </el-row>
    </el-main>
    <el-dialog
      title="产品介绍"
      :visible.sync="centerDialogVisible"
      :show-close="false"
      :center="true"
      @open="openDialog"
      :before-close="handleClose">
      <img :src="item.oneItem" class="image">
      <span style="padding: 10px;">这是详情描述</span>
      <span slot="footer" class="dialog-footer">
<!--    <el-button @click="dialogVisible = false">取 消</el-button>-->
    <el-button type="primary" @click="centerDialogVisible = false">关 闭</el-button>
  </span>
    </el-dialog>
  </el-container>

</template>

<script>
import Vue from "vue";

export default {
  name: 'ListPage',
  props: {
    dataSource: {
      type: Array,
      required: true
    }
  },

  data() {
    return {
      centerDialogVisible: false,
      item:{
        oneItem:null
      }
    };

  },
  methods: {
    handleClose(done) {
      // this.$confirm('确认关闭？')
      //   .then(_ => {
           done();
      //   })
      //   .catch(_ => {});
    },
    handleClick(inItem){
      this.centerDialogVisible = true;
      this.$set(this.item, 'oneItem', inItem.imgSrc)

    }

  },
  computed:{

  }
}
</script>

<style scoped>
.el-main {
  padding: 0;
}
.el-col {
  margin-top: 2rem;
}
.image {
  width: 100%;
  height: 10rem;
  display: block;
}
.el-card p,
.el-card strong {
  width: 100%;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  display: inline-block;
}
.el-card p {
  color: #666;
  margin-bottom: 0;
  font-size: .8rem;
}
</style>
