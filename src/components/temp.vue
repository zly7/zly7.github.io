<script lang="ts" setup>
    // import { time } from 'console';
    import type { FormInstance } from 'element-plus'
    import { ref ,reactive} from 'vue';
    
    defineProps({
      msg: String
    })
    
    
    const ruleFormRef = ref<FormInstance>()
    
    const checkAge = (rule: any, value: any, callback: any) => {
      if (!value) {
        return callback(new Error('Please input the age'))
      }
      setTimeout(() => {
        if (!Number.isInteger(value)) {
          callback(new Error('Please input digits'))
        } else {
          if (value < 18) {
            callback(new Error('Age must be greater than 18'))
          } else {
            callback()
          }
        }
      }, 1000)
    }
    
    const validatePass = (rule: any, value: any, callback: any) => {
      if (value === '') {
        callback(new Error('Please input the password'))
      } else {
        if (ruleForm.checkPass !== '') {
          if (!ruleFormRef.value) return
          ruleFormRef.value.validateField('checkPass', () => null)
        }
        callback()
      }
    }
    const validatePass2 = (rule: any, value: any, callback: any) => {
      if (value === '') {
        callback(new Error('Please input the password again'))
      } else if (value !== ruleForm.pass) {
        callback(new Error("Two inputs don't match!"))
      } else {
        callback()
      }
    }
    
    const ruleForm = reactive({
      pass: '',
      checkPass: '',
      age: '',
    })
    
    const rules = reactive({
      pass: [{ validator: validatePass, trigger: 'blur' }],
      checkPass: [{ validator: validatePass2, trigger: 'blur' }],
      age: [{ validator: checkAge, trigger: 'blur' }],
    })
    
    const submitForm = (formEl: FormInstance | undefined) => {
      if (!formEl) return
      formEl.validate((valid) => {
        if (valid) {
          console.log('submit!')
        } else {
          console.log('error submit!')
          return false
        }
      })
    }
    
    const resetForm = (formEl: FormInstance | undefined) => {
      if (!formEl) return
      formEl.resetFields()
    }
    
    function Course(CourseName, CourseCode, Language, Teacher, date, time_in) {
      this.CourseName = CourseName;
      this.CourseCode = CourseCode;
      this.Language = Language;
      this.Teacher = Teacher;
      this.Date = date;
      this.Time = time_in;
    }
    const courses = [
      new Course('OOAD', 'cs309', 'English', 'ZYQ', '2022/09/30', '19:00'),
      new Course('OOAD', 'cs309', 'English', 'ZYQ', '2022/09/30', '19:00')
    ];
    
    
    const count = ref(0)
    </script>
    <template>
    
      <p>
        <html lang="en">
    
        <head>
          <meta charset="UTF-8" />
          <title>Flight list</title>
        </head>
    
        <body>
          <ul>
            <li v-for="item in courses">
              <span v-for="c, k ,i in item">
                <!-- ????????????span????????? -->
    
                {{" "}} {{ c }} {{" "}}
    
    
              </span>
              <el-button>delete</el-button>
            </li>
    
          </ul>
        </body>
    
        </html>
      </p>
      <!-- ??????ref?????? -->
      <el-form
        ref="ruleFormRef"
        :model="ruleForm"
        status-icon
        :rules="rules"
        label-width="120px"
        class="demo-ruleForm"
      >
        <el-form-item label="Password" prop="pass">
          <el-input v-model="ruleForm.pass" type="password" autocomplete="off" />
        </el-form-item>
        <el-form-item label="Confirm" prop="checkPass">
          <el-input
            v-model="ruleForm.checkPass"
            type="password"
            autocomplete="off"
          />
        </el-form-item>
        <el-form-item label="Age" prop="age">
          <el-input v-model.number="ruleForm.age" />
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="submitForm(ruleFormRef)"
            >Submit</el-button
          >
          <el-button @click="resetForm(ruleFormRef)">Reset</el-button>
        </el-form-item>
      </el-form>
    
    
    
    </template>
    
    
    
    <style scoped>
    .read-the-docs {
      color: #888;
    }
    </style>
    