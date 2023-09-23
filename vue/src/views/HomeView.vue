<template>
  <div>
    主页
    <el-button>默认按钮</el-button>
    <el-button type="primary">主要按钮</el-button>
    <div>
      <el-input v-model="input" placeholder="请输入内容"></el-input>
    </div>
    <div>
      <el-autocomplete
        style="width: 300px"
        placeholder="请输入内容，我来帮你猜一猜"
        :fetch-suggestions="querySearch"
        :trigger-on-focus="false"
        v-model="value3"
      ></el-autocomplete>
    </div>

    <div>
      <el-select v-model="value" placeholder="请选择">
        <el-option value="青哥哥"></el-option>
        <el-option value="亲哥哥"></el-option>
        <el-option value="情哥哥"></el-option>
      </el-select>

      <el-select v-model="value" placeholder="请选择">
        <el-option
          v-for="item in coffees"
          :key="item.value"
          :label="item.label"
          :value="item.value"
        >
        </el-option>
      </el-select>
    </div>
    <div>
      <el-table
        :data="tableData"
        border
        :header-cell-style="{ background: 'aliceblue', fontSize: '16px' }"
      >
        <el-table-column
          label="序号"
          prop="id"
          align="center"
        ></el-table-column>
        <el-table-column
          label="名称"
          prop="name"
          align="center"
        ></el-table-column>
        <el-table-column
          label="年龄"
          prop="age"
          align="center"
        ></el-table-column>
        <el-table-column
          label="地址"
          prop="address"
          align="center"
        ></el-table-column>
        <el-table-column label="操作">
          <template v-slot="scope">
            <el-button type="primary" @click="edit(scope.row)">编辑</el-button>
          </template>
        </el-table-column>
      </el-table>
    </div>
  </div>
</template>

<script>
export default {
  name: "HomeView",
  data() {
    return {
      input: "",
      value: "",
      value3:"",
      coffees: [
        { value: "1星巴克咖啡" },
        { value: "1栖巢咖啡" },
        { value: "2瑞幸咖啡" },
        { value: "3库迪咖啡" },
      ],
      // 值必须带value
      tableData: [
        { name: "青哥哥哥", address: "安徽省合肥市", id: 1, age: "30" },
        { name: "青哥哥哥", address: "安徽省合肥市", id: 1, age: "30" },
        { name: "青哥哥哥", address: "安徽省合肥市", id: 1, age: "30" },
        { name: "青哥哥哥", address: "安徽省合肥市", id: 1, age: "30" },
        { name: "青哥哥哥", address: "安徽省合肥市", id: 1, age: "30" },
        { name: "青哥哥哥", address: "安徽省合肥市", id: 1, age: "30" },
        { name: "青哥哥哥", address: "安徽省合肥市", id: 1, age: "30" },
      ],
    };
  },
  methods: {
    querySearch(query, cb) {
      // callback
      let result = query
        ? this.coffees.filter((v) => v.value.includes(query))
        : this.coffees;
      console.log(result);
      cb(result);
    },
  },
};
</script>

<style scoped></style>
