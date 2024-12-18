<script setup lang="ts">
import { onMounted, ref } from 'vue';

const prop = defineProps(['data'])
const url = ref("")
onMounted(() => {
    url.value = location.href
})
</script>

<template>
    <div style="display: flex; flex-flow: column;">
        <div>
            <span style="font-weight: bold;">文章作者：</span>
            <span>{{ data.UserName }}</span>
        </div>
        <div style="margin-top: 0.5em;">
            <span style="font-weight: bold;">文章链接：</span>
            <a :href="url" style="color:rgb(0, 225, 225)">{{ url }}</a>
        </div>
        <div style="margin-top: 0.5em;">
            <span style="font-weight: bold;">版权声明：#</span>
            <span>本博客所有文章除特别声明外，均采用 </span>
            <a href="#" style="color:rgb(0, 225, 225)">CC BY-NC-SA 4.0</a>
            <span> 许可协议。转载请注明文章出处。</span>
        </div>
    </div>
</template>