<template>
    <div id="sidebar-left">
      <el-menu
        :collapse="collapse"
        class="el-menu-vertical-demo"
        background-color="#428BCA"
        text-color="#fff"
        active-text-color="#fff"
        unique-opened router>
        <template v-for="(item,index) in sidebarInfo">
            <el-submenu :index="item.index" :key="item.index" v-if="item.subNav">
              <template slot="title">
                <i :class="item.icon"></i>
                <span>{{item.title}}</span>
              </template>
              <el-menu-item-group>
                <!--<template slot="title">分组一</template>-->
                <el-menu-item :index="list.index" v-for="(list,index) in item.subNav" :key="list.index">{{list.title}}</el-menu-item>
              </el-menu-item-group>
            </el-submenu>
            <el-menu-item :index="item.index" :key="item.index" v-else>
              <template>
                <i :class="item.icon"></i>
                <span slot="title">{{item.title}}</span>
              </template>
            </el-menu-item>
        </template>
      </el-menu>

    </div>
</template>

<script>
  import {mapState,mapActions} from 'vuex'
    export default {
        name: 'sidebar',
        data () {
            return {
              indexPath:[],//保存点击过的页面路由信息
              sidebarInfo:[//左侧导航条信息
                {
                  icon: 'el-icon-setting',
                  index: 'test',
                  title: '测试数据库'
                },
                {
                  icon: 'el-icon-setting',
                  index: 'excel',
                  title: '测试案例'
                },
                {
                  icon: 'el-icon-setting',
                  index: 'testPlan',
                  title: '测试调度'
                },
                {
                  icon: 'el-icon-setting',
                  index: 'chart',
                  title: '测试进度'
                },

                // /**
                //  * inquiry 原始单据
                //  * **/
                // {
                //   icon: 'el-icon-tickets',
                //   index:'1',
                //   title: '原始单据',
                //   subNav:[
                //     {
                //       index:'/orderReceivable',
                //       title:'应收单据'
                //     },
                //     {
                //       index:'/transactionFlow',
                //       title:'交易流水'
                //     },
                //     {
                //       index:'/systemStatement',
                //       title:'系统对账单'
                //     },
                //     {
                //       index:'/bankFlow',
                //       title:'银行流水'
                //     }
                //   ]
                // },
                // /**
                //  * verifyPlatform 对账平台
                //  * **/
                // {
                //   icon: 'el-icon-date',
                //   index:'2',
                //   title: '财务对账',
                //   subNav:[
                //     {
                //       index: '/verifyReceivables',
                //       title: '收款对账'
                //     },
                //     {
                //       index: '/verifyAutomate',
                //       title: '自动对账'
                //     },
                //     {
                //       index:'/verifyBankStatement',
                //       title:'银行对账'
                //     }
                //   ]
                // },
                // /**
                //  * verifyRecord 对账记录
                //  * **/
                // {
                //   icon: 'el-icon-goods',
                //   title: '对账记录',
                //   index:'3',
                //   subNav:[
                //     {
                //       index:'/verifyReceivablesRecord',
                //       title:'收款记录'
                //     },
                //     {
                //       index:'/verifyBankStatementRecord',
                //       title:'银行记录'
                //     }
                //   ]
                // },
                // /**
                //  * reportForms报表
                //  * **/
                // {
                //   icon: 'el-icon-star-off',
                //   title: '月结报表',
                //   index:'4',
                //   subNav:[
                //     {
                //       index:'/OrderSummary',
                //       title:'订单执行总表'
                //     },
                //     {
                //       index:'/ReceivablesBalance',
                //       title:'收款对账余额表'
                //     }
                //   ]
                // },
                // {
                //   icon: 'el-icon-more',
                //   title: '系统设置',
                //   index:'5',
                //   subNav:[
                //     {
                //       index:'/Structure',
                //       title:'平台管理'
                //     },
                //     {
                //       index:'/UpdatePWD',
                //       title:'修改密码'
                //     },
                //     {
                //       index:'13',
                //       title:'系统设置'
                //     },
                //   ]
                // },
              ]
            }
        },
      computed:{
        ...mapState({
          collapse:state=>state.collapse
        }),
//        collapse(){
//          return this.$store.state.collapse
//        },
      },
      methods:{

      },
    }
</script>
<style scoped>

</style>
