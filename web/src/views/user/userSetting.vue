<script setup lang="ts">
import PageHeader from '@/layouts/PageHeader.vue';
import { reactive, ref } from 'vue';
import passwordEdit from './passwordEdit.vue';
import userDialogDelete from "./userDialogDelete.vue"
import router from '@/router';
const dialog = ref();

const dialogDelete = ref();


</script>

<template>
    <div>
        <el-card>
            <PageHeader />
        </el-card>
        <el-card>
            <el-row justify="space-between" style="margin-bottom: 30px;">
                <span>密码</span>
                <el-button type="primary" @click="dialog.openDialog()">修改密码</el-button>
            </el-row>
            <el-row justify="space-between">
                <span>注销</span>
                <el-button type="danger" @click="dialogDelete.openDialog()">账号注销</el-button>
            </el-row>
            <passwordEdit ref="dialog" />
        </el-card>

        <userDialogDelete ref="dialogDelete"></userDialogDelete>
    </div>
</template>

<style scoped>
.el-card {
    width: 60vw;
}
</style>