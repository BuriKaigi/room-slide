<template>
  <div></div>
</template>

<script setup lang="ts">
import { onMounted } from 'vue'

const MAX_PAGE = 12;

onMounted(() => {
  // 一定時間ごとにページを切り替える
  const cycle = (page) => {
    $slidev.nav.go(page);

    // 長めに表示するページ
    // ページごとの表示時間
    const LONG_VIEW_PAGES = [
      1, // トップ
      11, // ハッシュタグ
      12, // 注意事項∏
    ];

    setTimeout(() => cycle(page % MAX_PAGE + 1), LONG_VIEW_PAGES.includes(page) ? 10000 : 6000);
  }

  cycle(1);
})
</script>