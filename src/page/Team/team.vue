<template>
  <div class="goods">
  <el-container >
      <el-aside width="200px" style="padding-left: 20px">
        <el-menu>
          <el-menu-item index="1">
              <li class="left-nav">
             <i class="el-icon-user"></i>
              <span @click="team1" slot="title">学术骨干</span>
          </li>
          </el-menu-item>
           <el-menu-item index="2">
              <li class="left-nav">
             <i class="el-icon-user"></i>
              <span @click="team2" slot="title">固定研究人员</span>
          </li>
          </el-menu-item>
           <el-menu-item index="3">
              <li class="left-nav">
             <i class="el-icon-user"></i>
              <span @click="team3" slot="title">流动研究人员</span>
          </li>
          </el-menu-item>
        </el-menu>

      </el-aside>
   <div class="row" style="height: 1000px;">
        <div class="col-md-6" style="height: 1000px">
          <div class="box box-default" style="height: 1000px">
            <div id="team1" class="box-header with-border" style="list-style: none;display: block;width: 1000px">
              <h3 class="box-title" style="display:inline;margin-left: 20px;margin-top: 10px">学术骨干</h3>
               <div class="form-group" style="margin-left: 20px;margin-top: 10px;width: 100%;">
                  <textarea class="form-control" style="width: 15%"  rows="8" cols="12" placeholder="照片" name="noticeContent"></textarea>
                  <textarea class="form-control" style="width: 80%"  rows="8" cols="12" placeholder="    王勇，……" name="noticeContent"></textarea>
                </div>
              <div class="form-group" style="margin-left: 20px;margin-top: 10px;width: 100%;">
                  <textarea class="form-control" style="width: 15%"  rows="8" cols="12" placeholder="照片" name="noticeContent"></textarea>
                  <textarea class="form-control" style="width: 80%"  rows="8" cols="12" placeholder="……" name="noticeContent"></textarea>
                </div>
              <div class="form-group" style="margin-left: 20px;margin-top: 10px;width: 100%;">
                  <textarea class="form-control" style="width: 15%"  rows="8" cols="12" placeholder="照片" name="noticeContent"></textarea>
                  <textarea class="form-control" style="width: 80%" rows="8" cols="12" placeholder="……" name="noticeContent"></textarea>
                </div>
            </div>
             <div id="team2" class="box-header with-border" style="list-style: none;display: none;width: 1000px">
              <h3 class="box-title" style="display:inline;margin-left: 20px;margin-top: 10px">固定研究人员</h3>
                <div class="form-group" style="margin-left: 20px;margin-top: 10px;width: 100%;">
                  <textarea class="form-control" style="width: 15%" rows="8" cols="12" placeholder="照片" name="noticeContent"></textarea>
                  <textarea class="form-control" style="width: 80%" rows="8" cols="12" placeholder="……" name="noticeContent"></textarea>
                </div>
              <div class="form-group" style="margin-left: 20px;margin-top: 10px;width: 100%;">
                  <textarea class="form-control" style="width: 15%"  rows="8" cols="12" placeholder="照片" name="noticeContent"></textarea>
                  <textarea class="form-control" style="width: 80%" rows="8" cols="12" placeholder="……" name="noticeContent"></textarea>
                </div>
              <div class="form-group" style="margin-left: 20px;margin-top: 10px;width: 100%;">
                  <textarea class="form-control" style="width: 15%"  rows="8" cols="12" placeholder="照片" name="noticeContent"></textarea>
                  <textarea class="form-control" style="width: 80%"  rows="8" cols="12" placeholder="……" name="noticeContent"></textarea>
                </div>
            </div>
             <div id="team3" class="box-header with-border" style="list-style: none;display: none;width: 1000px">
              <h3 class="box-title" style="display:inline;margin-left: 20px;margin-top: 10px">流动研究人员</h3>
                <div class="form-group" style="margin-left: 20px;margin-top: 10px;width: 100%;">
                  <textarea class="form-control" style="width: 15%"  rows="8" cols="12" placeholder="照片" name="noticeContent"></textarea>
                  <textarea class="form-control" style="width: 80%"  rows="8" cols="12" placeholder="……" name="noticeContent"></textarea>
                </div>
              <div class="form-group" style="margin-left: 20px;margin-top: 10px;width: 100%;">
                  <textarea class="form-control" style="width: 15%"  rows="8" cols="12" placeholder="照片" name="noticeContent"></textarea>
                  <textarea class="form-control" style="width: 80%"  rows="8" cols="12" placeholder="……" name="noticeContent"></textarea>
                </div>
              <div class="form-group" style="margin-left: 20px;margin-top: 10px;width: 100%;">
                  <textarea class="form-control" style="width: 15%" rows="8" cols="12" placeholder="照片" name="noticeContent"></textarea>
                  <textarea class="form-control" style="width: 80%" rows="8" cols="12" placeholder="……" name="noticeContent"></textarea>
                </div>
            </div>
            <!-- /.box-header -->
            <div class="box-body">

            </div>
            <!-- /.box-body -->
          </div>
          <!-- /.box -->
        </div>

    <div v-for="(item,i) in home" :key="i">

      <div class="activity-panel" v-if="item.type === 1">
        <ul class="box">
          <li class="content" v-for="(iitem,j) in item.panelContents" :key="j" @click="linkTo(iitem)">

            <a class="cover-link"></a>
          </li>
        </ul>
      </div>

      <section class="w mt30 clearfix" v-if="item.type === 2">
        <y-shelf :title="item.name">
          <div slot="content" class="hot">
            <mall-goods :msg="iitem" v-for="(iitem,j) in item.panelContents" :key="j"></mall-goods>
          </div>
        </y-shelf>
      </section>

      <section class="w mt30 clearfix" v-if="item.type === 3">
        <y-shelf :title="item.name">
          <div slot="content" class="floors" >
            <div class="imgbanner" v-for="(iitem,j) in item.panelContents" :key="j" v-if="iitem.type === 2 || iitem.type === 3" @click="linkTo(iitem)">
              <img v-lazy="iitem.picUrl">
              <a class="cover-link"></a>
            </div>
            <mall-goods :msg="iitem" v-for="(iitem,j) in item.panelContents" :key="j+'key'" v-if="iitem.type != 2 && iitem.type != 3"></mall-goods>
          </div>
        </y-shelf>
      </section>

      </div>
  </div>
    </el-container>
  </div>
</template>
<script>
  import { getAllGoods } from '@/api/goods'
  import { recommend } from '@/api/index'
  import mallGoods from '@/components/mallGoods'
  import YButton from '@/components/YButton'
  import YShelf from '@/components/shelf'
  export default {
    data () {
      return {
        goods: [],
        noResult: false,
        error: false,
        min: '',
        max: '',
        loading: true,
        timer: null,
        sortType: 1,
        windowHeight: null,
        windowWidth: null,
        recommendPanel: [],
        sort: '',
        currentPage: 1,
        total: 0,
        pageSize: 20
      }
    },
    methods: {
      handleSizeChange (val) {
        this.pageSize = val
        this._getAllGoods()
        this.loading = true
      },
      team1() {
        document.getElementById('team1').style.display = 'block'
        document.getElementById('team2').style.display = 'none'
        document.getElementById('team3').style.display = 'none'
      },
      team2() {
        document.getElementById('team2').style.display = 'block'
        document.getElementById('team1').style.display = 'none'
        document.getElementById('team3').style.display = 'none'
      },
      team3() {
        document.getElementById('team3').style.display = 'block'
        document.getElementById('team2').style.display = 'none'
        document.getElementById('team1').style.display = 'none'
      },
      handleCurrentChange (val) {
        this.currentPage = val
        this._getAllGoods()
        this.loading = true
      },
      _getAllGoods () {
        let cid = this.$route.query.cid
        if (this.min !== '') {
          this.min = Math.floor(this.min)
        }
        if (this.max !== '') {
          this.max = Math.floor(this.max)
        }
        let params = {
          params: {
            page: this.currentPage,
            size: this.pageSize,
            sort: this.sort,
            priceGt: this.min,
            priceLte: this.max,
            cid: cid
          }
        }
        getAllGoods(params).then(res => {
          if (res.success === true) {
            this.total = res.result.total
            this.goods = res.result.data
            this.noResult = false
            if (this.total === 0) {
              this.noResult = true
            }
            this.error = false
          } else {
            this.error = true
          }
          this.loading = false
        })
      },
      // 默认排序
      reset () {
        this.sortType = 1
        this.sort = ''
        this.currentPage = 1
        this.loading = true
        this._getAllGoods()
      },
      // 价格排序
      sortByPrice (v) {
        v === 1 ? this.sortType = 2 : this.sortType = 3
        this.sort = v
        this.currentPage = 1
        this.loading = true
        this._getAllGoods()
      }
    },
    watch: {
      $route (to, from) {
        if (to.fullPath.indexOf('/goods?cid=') >= 0) {
          this.cId = to.query.cid
          this._getAllGoods()
        }
      }
    },
    created () {
    },
    mounted () {
      this.windowHeight = window.innerHeight
      this.windowWidth = window.innerWidth
      this._getAllGoods()
      recommend().then(res => {
        let data = res.result
        this.recommendPanel = data[0]
      })
    },
    components: {
      mallGoods,
      YButton,
      YShelf
    }
  }
</script>
<style lang="scss" rel="stylesheet/scss" scoped>
  @import "../../assets/style/mixin";
  @import "../../assets/style/theme";

  .nav {
    height: 60px;
    line-height: 60px;
    > div {
      display: flex;
      align-items: center;
      a {
        padding: 0 15px;
        height: 100%;
        @extend %block-center;
        font-size: 12px;
        color: #999;
        &.active {
          color: #5683EA;
        }
        &:hover {
          color: #5683EA;
        }
      }
      input {
        @include wh(80px, 30px);
        border: 1px solid #ccc;
      }
      input + input {
        margin-left: 10px;
      }
    }
    .price-interval {
      padding: 0 15px;
      @extend %block-center;
      input[type=number] {
        border: 1px solid #ccc;
        text-align: center;
        background: none;
        border-radius: 5px;
      }
    }
  }

  .goods-box {
    > div {
      float: left;
      border: 1px solid #efefef;
    }
  }

  .no-info {
    padding: 100px 0;
    text-align: center;
    font-size: 30px;
    display: flex;
    flex-direction: column;
    .no-data{
      align-self: center;
    }
  }

  .img-item{
    display: flex;
    flex-direction: column;
  }

  .el-pagination{
    align-self: flex-end;
    margin: 3vw 10vw 2vw;
  }

  .section {
    padding-top: 8vw;
    margin-bottom: -5vw;
    width: 1218px;
    align-self: center;
  }

  .recommend {
    display: flex;
    > div {
      flex: 1;
      width: 25%;
    }
  }
.el-aside {
  background-color: #f5f5f5;
  color: #333;
  text-align: center;
  line-height: 200px;
}

.el-main {
  background-color: #ffffff;
  color: #333;
  text-align: center;
  line-height: 100px;
}

body > .el-container {
  margin-bottom: 40px;
}

.el-container:nth-child(5) .el-aside,
.el-container:nth-child(6) .el-aside {
  line-height: 260px;
}

.el-container:nth-child(7) .el-aside {
  line-height: 320px;
}

.el-container {
  padding: 0px;
  margin: 0px;
  height: 100%;
}
 .left-nav{
   height: 25px;
 }

</style>
