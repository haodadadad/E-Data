<template>
<div>
  <div style="margin: 10px 0">
    <el-input style="width: 200px" placeholder="请输入工号" suffix-icon="el-icon-search" v-model="userid"></el-input>
    <el-input style="width: 200px" placeholder="请输入姓名" suffix-icon="el-icon-search" class="ml-5"
              v-model="username"></el-input>
    <el-input style="width: 200px" placeholder="请输入班组" suffix-icon="el-icon-search" class="ml-5"
              v-model="userclass"></el-input>
    <el-button class="ml-5" type="primary" @click="load">搜索</el-button>
    <el-button class="ml-5" type="warning" @click="reset">重置</el-button>
  </div>

  <div style="margin: 10px 0">
    <el-button type="primary" @click="handleAdd">添加<i class="el-icon-circle-plus-outline"></i></el-button>

    <el-popconfirm title="确定批量删除这些记录吗" @confirm="delBatch" class="ml-5">
      <el-button type="danger" slot="reference">批量删除<i class="el-icon-remove-outline"></i></el-button>
    </el-popconfirm>

    <el-button type="primary" class="ml-5">导入<i class="el-icon-bottom"></i></el-button>
    <el-button type="primary">导出<i class="el-icon-top"></i></el-button>
  </div>

  <el-table :data="tableData" border stripe :header-cell-class-name="headerBg" @selection-change="handleSelectionChange">
    <el-table-column type="selection" width="55"/>
    <el-table-column prop="id" label="ID" width="140"></el-table-column>
    <el-table-column prop="userid" label="工号" width="140"></el-table-column>
    <el-table-column prop="username" label="姓名" width="140"></el-table-column>
    <el-table-column prop="userclass" label="班组" width="220"></el-table-column>
    <el-table-column label="操作">
      <template slot-scope="scope" class="ml-5">
        <el-button type="success" @click="handleEdit(scope.row)">编辑<i class="el-icon-edit"></i></el-button>
        <el-popconfirm title="确定删除这条记录吗" @confirm="handleDelete(scope.row.id)">


          <el-button type="danger" slot="reference" class="ml-5">删除<i class="el-icon-remove-outline"></i>
          </el-button>
        </el-popconfirm>
      </template>
    </el-table-column>
  </el-table>
  <div style="padding: 10px 0">
    <el-pagination
        @size-change="handleSizeChange"
        @current-change="handleCurrentChange"
        :current-page="pageNum"
        :page-sizes="[5,10,20]"
        :page-size="pageSize"
        layout="total, sizes, prev, pager, next, jumper"
        :total="total">
    </el-pagination>

  </div>

  <el-dialog :visible.sync="dialogFormVisible" title="用户信息" width="30%">
    <el-form label-width="80px" size="small">
      <el-form-item label="用户工号">
        <el-input v-model="form.userid" autocomplete="off"/>
      </el-form-item>
      <el-form-item label="用户姓名">
        <el-input v-model="form.username" autocomplete="off"/>
      </el-form-item>
      <el-form-item label="用户班组">
        <el-input v-model="form.userclass" autocomplete="off"/>
      </el-form-item>
    </el-form>
    <template #footer>
      <span class="dialog-footer">
        <el-button @click="dialogFormVisible = false">Cancel</el-button>
        <el-button type="primary" @click="save">Confirm</el-button
        >
      </span>
    </template>
  </el-dialog>
</div>
</template>

<script>
export default {
  name: "User",
  data(){
    return{

      tableData: [],
      total: 0,
      pageNum: 1,
      pageSize: 10,
      userid: "",
      username: "",
      userclass: "",
      multipleSelection: [],
      form: {},
      dialogFormVisible: false,
      headerBg: 'headerBg'
    }

  },
  created() {
    this.load()
  },
  methods:{
    load() {
      this.request.get("/user/page", {
        params: {
          pageNum: this.pageNum,
          pageSize: this.pageSize,
          userid: this.userid,
          username: this.username,
          userclass: this.userclass
        }
      }).then(res => {
        console.log(res)
        this.tableData = res.records
        this.total = res.total
      })
    },
    reset() {
      this.username = ""
      this.userid = ""
      this.userclass = ""
      this.load()
    },
    save() {
      this.request.post("/user", this.form).then(res => {
        if (res) {
          this.$message.success("保存成功")
          this.dialogFormVisible = false
          this.load()
        } else {
          this.$message.error("保存失败")
        }
      })

    },
    handleAdd() {
      this.dialogFormVisible = true
      this.form = {}
    },
    handleEdit(row) {
      this.form = Object.assign({}, row)
      this.dialogFormVisible = true
    },
    handleDelete(id) {
      this.request.delete("/user/" + id).then(res => {
        if (res) {
          this.$message.success("删除成功")
          this.load()
        } else {
          this.$message.error("删除失败")
        }
      })
    },
    handleSelectionChange(val) {
      console.log(val)
      this.multipleSelection = val
    },
    delBatch() {
      let ids = this.multipleSelection.map(v => v.id)  //[{},{},{}]=>[1,2,3]
      this.request.post("/user/del/batch", ids).then(res => {
        if (res) {
          this.$message.success("批量删除成功")
          this.load()
        } else {
          this.$message.error("批量删除失败")
        }
      })

    },
    handleSizeChange(pageSize) {
      console.log(pageSize)
      this.pageSize = pageSize
      this.load()
    },

    handleCurrentChange(pageNum) {
      console.log(pageNum)
      this.pageNum = pageNum
      this.load()
    },
  }
}
</script>

<style scoped>
.headerBg{
  background: #eee!important;
}
</style>