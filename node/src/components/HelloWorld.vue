<template>
  <div class="hello">
    <el-table
    :data="tableData"
    :height="500"
    border
    style="width: 500px">
    <el-table-column
      fixed
      prop="date"
      label="日期"
      width="auto">
    </el-table-column>
    <el-table-column
      prop="name"
      label="医院名称"
      width="auto">
    </el-table-column>
    <el-table-column
      prop="province"
      label="耗材名称"
      width="auto">
    </el-table-column>
    <el-table-column
      prop="city"
      label="价格"
      width="auto">
    </el-table-column>
    <el-table-column
      label="操作"
      width="auto">
      <template slot-scope="scope">
        <el-button @click="handleClick(scope.row)" type="text" size="small">查看</el-button>
      </template>
    </el-table-column>
  </el-table>
  <el-pagination
    :current-page="tablePagination.current"
    :page-size="tablePagination.size"
    :total="tablePagination.size"
    :page-sizes="[10, 20, 30 ,40]"
    layout="total, sizes, prev, pager, next"
    @current-change="handleCurrentChange"
    @size-change="handleSizeChange">
  </el-pagination>
  </div>
</template>

<script>
export default {
  name: 'TableCom',
  data () {
    return {
      tablePagination: {
        current: 1,
        size: 10,
        total: 0
      },
      tableData: [{
        date: '2016-05-02',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }]
    }
  },
  methods: {
    handleCurrentChange () {
      this.tablePagination.current = 1
    },
    handleSizeChange (size) {
      this.tablePagination.current = 1
      this.tablePagination.size = size
    }
  }
}
</script>
<style lang='less' scoped>
::v-deep .el-table thead.is-group th{
  background-color: pink;
  border: 1px solid #346688 !important;
}
.el-table--border,
.el-table--group {
  border-color: #346688;
}
.el-table--border::after,
.el-table--group::after,
.el-table::before {
  background-color: #346688;
}
.el-pagination {
  width: 500px;
  margin-top: 10px;
  text-align: center;
}
</style>
