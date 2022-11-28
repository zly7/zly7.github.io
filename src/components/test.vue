<template>
      <el-form ref="ruleFormRef" :model="ruleForm2" :rules="rules2" >
    <el-form-item label="Course Name" prop="CourseName">
      <el-input v-model="ruleForm2.CourseName" />
    </el-form-item>
    
  </el-form>
  {{ruleForm2.CourseName}}
  </template>
  
  <script lang="ts" setup>
  import { reactive, ref } from 'vue'
  import type { FormInstance } from 'element-plus'
  defineProps({
  msg: String
})
  const ruleFormRef = ref<FormInstance>()
  
  
  const validateName = (rule: any, value: any, callback: any) => {
    console.log(value)
    if (value === '') {
      callback(new Error('Please input the password'))
    } else {
        if (value < 18) {
        callback(new Error('Age must be greater than 18'))
      } else {
        callback()
      }
    }
  }

  
  const ruleForm2 = reactive({
  CourseName: '',
  CourseCode: 'XXX',
  Language: '',
  Teacher: 'XXX',
  Date: '',
  Time: '',
  Location: 'XXX',
  Duration: 'XXX',

});
  
  const rules2 = reactive({
    CourseName: [{ validator: validateName, trigger: 'blur' }],

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
  </script>
  