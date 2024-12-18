<template>
  <div>
    <el-dialog v-model="dialogDelete" title="您确定要注销账号吗？">
      <el-form v-model="formDelete" label-width="80px">
        <el-form-item label="账号密码">
          <el-input v-model="formDelete.Password" />
        </el-form-item>
        <el-form-item>
          <el-button type="danger" @click="submitDelete(formDelete)"
            >确认注销</el-button
          >
          <el-button @click="dialogDelete = false">取消</el-button>
        </el-form-item>
      </el-form>
    </el-dialog>
  </div>
</template>

<script setup lang="ts">
import { ref, reactive } from "vue";
import api from "@/api/api";
import { useRouter } from "vue-router";

const router = useRouter();

const dialogDelete = ref(false);

const formDelete = reactive({
  Password: "",
});
const submitDelete = async (data: any) => {
  try {
    console.log(data);
    const res = await api.deleteUser(data);
    localStorage.setItem("token", "");
    dialogDelete.value = false;
    router.push("/home");
  } catch (err) {
    console.error(err);
  }
};

const openDialog = ()=>{
    dialogDelete.value = true
}
defineExpose({
    openDialog
})
</script>

<style scoped></style>
