<template>
  <div id="app">
    <el-button type="text" @click="dialogVisible = true"
      >点击打开 Dialog</el-button
    >
    <el-button type="text" @click="dialogVisible = true"
      >点击打开 Dialog</el-button
    >
    <el-dialog
      title="提示"
      :visible.sync="dialogVisible"
      width="50%"
    >
    <el-form ref="form" :model="form">
      <el-table  ref="table" :data="form.tableData" empty-text='暂无数据'>
        <el-table-column label="编号" type="index" width="80">
       
        </el-table-column>
        <el-table-column label="子域名称" width="auto">
          <template slot-scope="scope">
            <el-form-item >
              <el-input v-model="scope.row.name"></el-input>
            </el-form-item>
          </template>
        </el-table-column>
        <el-table-column label="子域描述" width="auto">
          <template slot-scope="scope">
            <el-form-item >
              <el-input v-model="scope.row.description"></el-input>
            </el-form-item>
          </template>
        </el-table-column>
        <el-table-column  label="操作" width="180">
          <template slot-scope="scope">
            <el-button type="danger" size="mini" @click="del(scope.$index)" v-show="length>1" icon='el-icon-delete'></el-button>
            <el-button type="primary" size="mini" @click="add" icon='el-icon-plus'></el-button>
          </template>
        </el-table-column>
      </el-table>
    </el-form>

      <span slot="footer" class="dialog-footer">
        <el-button @click="dialogVisible = false">取 消</el-button>
        <el-button type="primary" @click="dialogVisible = false"
          >确 定</el-button
        >
      </span>
    </el-dialog>
  </div>
</template>

<script>
export default {
  name: "",
  components: {},
  created(){
  },
  computed:{
    length: function () {
    return this.form.tableData.length;
  }
  },
  data() {
    return {
        dialogVisible: false,
        form:{
            tableData:[
                {
            name: "",
            description: ""
          },
            ]
        }
    };
  },
  methods: {

    add(){
          this.form.tableData.push({
              name: "",
              description: ''
          })
      },
      del(index){
          this.form.tableData.splice(index,1);
      }
  },
};
</script>

<style></style>
