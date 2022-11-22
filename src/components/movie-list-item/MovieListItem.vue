<template>
  <li
    class="list-group-item"
    :class="[{ like: movie.like }, { favourite: movie.favourite }]"
  >
    <span
      class="list-group-item-label"
      @click="$emit('onToggle', { id: movie.id, prop: 'like' })"
      >{{ movie.name }}</span
    >
    <input type="nuber" class="list-group-item-input" :value="movie.viewers" />
    <div class="d-flex justify-content-center align-items-center">
      <button
        type="button"
        class="btn-cookie btn-sm"
        @click="$emit('onToggle', { id: movie.id, prop: 'favourite' })"
      >
        <i class="fas fa-cookie"></i>
      </button>
      <button
        type="button"
        class="btn-trash btn-sm"
        @click="$emit('onRemove', movie.id)"
      >
        <i class="fas fa-trash"></i>
      </button>
      <i class="fas fa-star"></i>
    </div>
  </li>
</template>

<script>
export default {
  props: {
    movie: {
      type: Object,
      required: true,
    },
  },
  methods: {
    onLike() {
      this.$emit("onLike", this.movie.id);
    },
  },
};
</script>

<style scoped>
.list-group-item {
  padding: 15px 20px;
  border: none;
  border-bottom: 1px solid #3d5a80;
  display: flex;
  justify-content: space-between;
}
.list-group-item:last-child {
  border-bottom: none;
}
.list-group-item span {
  line-height: 35px;
  font-size: 20px;
  cursor: pointer;
  widows: 550px;
  width: 50%;
}
.list-group-item input {
  line-height: 35px;
  font-size: 20px;
  text-align: center;
  border: none;
  outline: none;
}
.list-group-item button {
  width: 35px;
  height: 35px;
  margin: 3px;
  font-size: 17px;
  border: none;
  cursor: pointer;
}
.list-group-item button.btn-cookie {
  color: #e0913e;
}
.list-group-item button.btn-trash {
  color: #e5383b;
}
.list-group-item .fa-star {
  width: 35px;
  height: 35px;
  text-align: center;
  line-height: 35px;
  font-size: 16px;
  color: #ffd700;
  transition: 0.3s all;
  transform: translateX(30px);
  opacity: 0;
}

.list-group-item.like .fa-star {
  opacity: 1;
  transform: translateX(0);
}

.list-group-item.favourite .list-group-item-label,
.list-group-item.favourite .list-group-item-input {
  color: #e09f3e;
}
</style>
