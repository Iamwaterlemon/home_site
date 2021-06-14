<template>
  <el-container :class="containerClass">
    <el-main>
        <common-main @clickSideMenu="handleSideClick" :title="imgLabel" :menus="sideMenus">
          <div  slot="content">
            <list-page :dataSource="dataSource"></list-page>
          </div>
        </common-main>

      <div>
      <h2>敬业科技</h2>
      </div>
    <div class="img-box">
      <img src="/static/img/home1.jpg" alt="company-concept">
    </div>
    </el-main>
  </el-container>
</template>

<script>
import ListPage from "../../productpage/components/List";
import CommonBanner from '../../common/Banner'
import CommonMain from '../../common/Main'

export default {
  name: 'HomeMain',
  computed: {
    containerClass () {
      return this.$ISMOBILE ? '' : 'container'
    }
  },
  components:{
    CommonBanner,
    CommonMain,
    ListPage
  },
  data () {
    return {
      imgPath: '/static/img/banner3.jpg',
      imgLabel: '产品与服务',
      dataSource: [
        {
          id: 'product1',
          imgSrc: '/static/img/product1.jpg',
          label: '产品名称'
        },
        {
          id: 'product2',
          imgSrc: '/static/img/product2.jpg',
          label: '产品名称'
        },
        {
          id: 'product3',
          imgSrc: '/static/img/product1.jpg',
          label: '产品名称'
        },
        {
          id: 'product4',
          imgSrc: '/static/img/product2.jpg',
          label: '产品名称'
        },
        {
          id: 'product5',
          imgSrc: '/static/img/product1.jpg',
          label: '产品名称'
        },
        {
          id: 'product6',
          imgSrc: '/static/img/product2.jpg',
          label: '产品名称'
        }
      ],
      sideMenus: [
        {
          id: 'side1',
          key: 'ProductList',
          label: '产品列表'
        },
        {
          id: 'side2',
          key: 'ServiceList',
          label: '服务列表'
        }
      ],
      activeComponentName: 'ProductList'
    }
  },
  methods: {
    handleSideClick(name) {
      this.activeComponentName = name
      if (name === 'ProductList') {
        this.dataSource = [
          {
            id: 'product1',
            imgSrc: '/static/img/product1.jpg',
            label: '产品名称'
          },
          {
            id: 'product2',
            imgSrc: '/static/img/product2.jpg',
            label: '产品名称'
          },
          {
            id: 'product3',
            imgSrc: '/static/img/product1.jpg',
            label: '产品名称'
          },
          {
            id: 'product4',
            imgSrc: '/static/img/product2.jpg',
            label: '产品名称'
          },
          {
            id: 'product5',
            imgSrc: '/static/img/product1.jpg',
            label: '产品名称'
          },
          {
            id: 'product6',
            imgSrc: '/static/img/product2.jpg',
            label: '产品名称'
          }
        ]
      } else if (name === 'ServiceList') {
        this.dataSource = [
          {
            id: 'service1',
            imgSrc: '/static/img/home1.jpg',
            label: '服务名称'
          },
          {
            id: 'service2',
            imgSrc: '/static/img/home1.jpg',
            label: '服务名称'
          },
          {
            id: 'service3',
            imgSrc: '/static/img/home1.jpg',
            label: '服务名称'
          },
          {
            id: 'service4',
            imgSrc: '/static/img/home1.jpg',
            label: '服务名称'
          }
        ]
      } else {
        this.dataSource = []
      }
    }
  }
}
</script>

<style scoped>
  .container{
    padding: 0 1rem;
  }
  .el-container p {
    line-height: 1.5;
    text-align: justify;
  }
  .img-box {
    padding: 2rem 0;
  }
  .img-box img {
    height: 40rem;
    width: 100%;
  }

  .el-row {
    padding: 2rem 0;
  }
</style>
