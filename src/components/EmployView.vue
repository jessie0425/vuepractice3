<template>
  <div id="employ">
    <el-row :gutter="20">
      <el-col :span="12" :offset="6">
        <fieldset>
          <legend>指令綜合小練習</legend>
          <el-form :model="newPerson" :rules="rules" ref="newPerson" label-width="100px" class="demo-ruleForm">
            <el-form-item label="姓名" prop="name">
              <el-input v-model="newPerson.name"></el-input>
            </el-form-item>
            <el-form-item label="年齡" prop="age">
              <el-input v-model.number="newPerson.age"></el-input>
            </el-form-item>
            <el-form-item label="性別" prop="sex">
              <el-select v-model="newPerson.sex" placeholder="請選擇性別">
                <el-option label="男" value="男"></el-option>
                <el-option label="女" value="女"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="手機" prop="phone">
              <el-input v-model.number="newPerson.phone"></el-input>
            </el-form-item>
            <el-form-item>
              <el-button type="primary" @click="add('newPerson')">創建新用戶</el-button>
            </el-form-item>
          </el-form>
        </fieldset>
        <el-table
            :data="persons"
            style="width: 100%">
          <el-table-column
              prop="name"
              label="姓名"
              width="180">
          </el-table-column>
          <el-table-column
              prop="age"
              label="年齡"
              width="180">
          </el-table-column>
          <el-table-column
              prop="sex"
              label="性別">
          </el-table-column>
          <el-table-column
              prop="phone"
              label="手機">
          </el-table-column>
          <el-table-column label="操作">
            <el-button
              size="mini"
              type="danger"
              @click="del(i)">删除
            </el-button>
          </el-table-column>
        </el-table>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  name:'EmployView',
  data() {
    return{
      rules: {
        name: [
          { required: true, message: '請輸入姓名', trigger: 'blur' },
        ],
        age: [
          { required: true, message: '年齡不能為空'},
          { type: 'number', message: '年齡必須為數值'}
        ],
        sex: [
          { required: true, message: '請選擇性別', trigger: 'change' }
        ],
        phone: [
          { type: 'number', required: true, message: '請輸入電話', trigger: 'change' }
        ]
      },
      persons:[
        {name:'張三', age:18, sex:'男', phone:'0911112304'},
        {name:'李四', age:28, sex:'女', phone:'0912112314'},
        {name:'王五', age:38, sex:'男', phone:'0911312324'},
        {name:'趙六', age:48, sex:'女', phone:'0914112344'},
        {name:'李七', age:58, sex:'男', phone:'0911512354'},
      ],
      newPerson:{name:'', age:0, sex:'男', phone:''}
    }
  },
  methods: {
    add(formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          alert('submit!');

          const { name, age, sex, phone } = this.newPerson
          console.log(name, age, sex, phone) // 有空再篩選手機格式
          if(!name || !age || !phone){
            alert('請勿新增空資料')
            return
          }
          this.persons.unshift({...this.newPerson})
          this.newPerson = { name: '', age: 0, sex: '男', phone: '' };
        } else {
          console.log('error submit!!');
          return false;
        }
      });
    },
    del(index){
      this.persons.splice(index, 1)
    }
  }
}
</script>

