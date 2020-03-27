<template>
  <div class="hundun-editor-app-wrapper">
    <div class="hundun-editor-tool-box">
      <div class="hundun-editor-tool-box-item">正文</div>
      <div class="hundun-editor-tool-box-item">图片</div>
    </div>
    <div class="hundun-editor-content" ref="editorRef" contenteditable="true"></div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted } from "@vue/composition-api";
export default defineComponent({
  components: {},
  setup() {
    const editorRef = ref<HTMLElement>("");
    onMounted(() => {
      editorRef.value.onkeydown = function(e: KeyboardEvent) {
        if (e.keyCode === 13) {
          // 回车插入段落
          console.log(1)
          document.execCommand("insertHTML", false, "<p><br></p>");
        }
      };
    });
    return {
      editorRef
    };
  }
});
</script>

<style>
@import "./app.scss";
</style>
