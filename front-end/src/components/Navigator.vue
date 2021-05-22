<template>
  <div class="navigator">
    <!-- Criar componente inteligente para filtrar -->
    <i class="fas fa-chevron-left"></i>Minha conta
  </div>
</template>

<script>
export default {
  name: "Navigator",
};
</script>

<style lang="scss" scoped>
.navigator {
  background: white;
  color: #18acc4;
  font-weight: bold;
  padding: 20px 15px;
  i {
    padding-right: 10px;
  }
}
</style>
