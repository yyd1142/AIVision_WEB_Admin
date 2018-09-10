<template>
  <div>
    <RootPage :language="language" default-active="1-1" :default-openeds="['1']">
      <div class="Configuration" slot="page">
        <div class="form-cell">
          <div class="form-item">
            <el-input :placeholder="languageDatas.SearchStore[language]"
                      v-model="form.username" style="width: 240px;">
            </el-input>
          </div>
          <div class="form-item right">
            <el-button type="primary" icon="el-icon-plus" style="width: 240px;">
              {{languageDatas.NewStore[language]}}
            </el-button>
          </div>
        </div>
        <div class="table-cell my-box-shadow">
          <el-table
            :data="tableData"
            style="width: 100%"
            :default-sort="{prop: 'date', order: 'descending'}"
          >
            <el-table-column
              prop="name"
              :label="languageDatas.StoreName[language]"
              sortable
              width="180">
            </el-table-column>
            <el-table-column
              prop="role"
              :label="languageDatas.AffiliatedHeadOffice[language]"
              sortable
              width="200">
            </el-table-column>
            <el-table-column
              prop="admin"
              :label="languageDatas.Administrators[language]"
              sortable
              width="180">
            </el-table-column>
            <el-table-column
              prop="stroe"
              :label="languageDatas.ShopSign[language]"
              sortable
              width="180">
            </el-table-column>
            <el-table-column
              prop="status"
              :label="languageDatas.OpenState[language]"
              sortable
              width="180">
            </el-table-column>
            <el-table-column
              prop="status"
              :label="languageDatas.OpenDate[language]"
              sortable
              width="180">
            </el-table-column>
            <el-table-column
              prop="status"
              :label="languageDatas.DueDate[language]"
              sortable
              width="180">
            </el-table-column>
            <el-table-column
              fixed="right"
              :label="languageDatas.Option[language]">
              <template slot-scope="scope">
                <el-button type="text" size="small" style="color: #ff0514">{{languageDatas.DisableAccount[language]}}
                </el-button>
              </template>
            </el-table-column>
          </el-table>
        </div>
      </div>
    </RootPage>
  </div>
</template>

<script>
  import RootPage from "@pages/index.vue";
  import {TitleCell, MyFormCell, DataDetailCell, DataDetailTitle} from "@components";

  export default {
    name: "Configuration",
    components: {
      RootPage,
      TitleCell,
      MyFormCell,
      DataDetailCell,
      DataDetailTitle
    },
    computed: {
      languageDatas() {
        return this.$store.getters.languageDatas;
      },
    },
    async asyncData(ctx) {
      const language = ctx.query.language || 'en';
      return {
        language: language,
        form: {
          username: ''
        },
        tableData: [
          {
            date: '2016-05-02',
            name: '王小虎',
            role: '店员',
            admin: 'Administrators',
            stroe: '广州分公司',
            status: '正常'
          }, {
            date: '2016-05-04',
            name: '王小虎',
            role: '店员',
            admin: 'Administrators',
            stroe: '广州分公司',
            status: '正常'
          }, {
            date: '2016-05-01',
            name: '王小虎',
            role: '店员',
            admin: 'Administrators',
            stroe: '广州分公司',
            status: '正常'
          }, {
            date: '2016-05-03',
            name: '王小虎',
            role: '店员',
            admin: 'Administrators',
            stroe: '广州分公司',
            status: '正常'
          }
        ]
      }
    },
    mounted() {

    },
    methods: {
      formatter(row, column) {
        return row.address;
      },
      handleClick(row) {
        console.log(row);
      }
    }
  }
</script>

<style lang="less">
  .Configuration {
    width: 100%;
    display: flex;
    display: -webkit-flex; /* Safari */
    padding: 0 15px 30px 15px;
    flex-direction: column;
    .my-box-shadow {
      -moz-box-shadow: 0px 1px 5px #ccc; /* 老的 Firefox */
      box-shadow: 0px 1px 5px #ccc;
    }
    .form-cell {
      width: 100%;
      display: flex;
      display: -webkit-flex; /* Safari */
      flex-direction: row;
      height: 80px;
      .form-item {
        width: 100% / 2;
        display: flex;
        display: -webkit-flex; /* Safari */
        align-items: center;
        &.right {
          justify-content: flex-end;
        }
      }
    }
  }
</style>
