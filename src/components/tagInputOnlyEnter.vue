<template>
  <renderless-tags-input
    :value="value"
    @input="
      (tags) => {
        $emit('input', tags);
      }
    "
  >
    <div
      slot-scope="{ tags, removeTag, inputAttrs, inputEvents }"
      class="tags-input"
    >
      <span class="tags-input-tag" v-for="tag in tags" :key="tag">
        <span>{{ tag }}</span>
        <button type="button" class="tags-input-remove" @click="removeTag(tag)">
          &times;
        </button>
      </span>

      <input
        class="tags-input-text"
        placeholder="Add tag..."
        v-bind="inputAttrs"
        v-on="inputEvents"
      />
    </div>
  </renderless-tags-input>
</template>

<script>
import renderlessTagsInput from "@/components/renderless/renderless_tags_input.vue";
export default {
  name: "tagInputOnlyEnter",
  components: {
    renderlessTagsInput,
  },
  props: ["value"],
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.tags-input {
  display: flex;
  flex-wrap: wrap;
  background-color: lightgray;
  border-width: 1px;
  border-radius: 0.25rem;
  padding-left: 0.5rem;
  padding-right: 1rem;
  padding-top: 0.5rem;
  padding-bottom: 0.25rem;
}

.tags-input-tag {
  display: inline-flex;
  line-height: 1;
  align-items: center;
  font-size: 0.875rem;
  border-color: #bcdefa;
  background-color: #2779bd;
  color: #fff;
  border-radius: 0.25rem;
  user-select: none;
  padding: 0.25rem;
  margin-right: 0.5rem;
  margin-bottom: 0.25rem;
}

.tags-input-tag:last-of-type {
  margin-right: 0;
}

.tags-input-remove {
  color: #bcdefa;
  font-size: 1.125rem;
  line-height: 1;
  background-color: #2779bd;
  border: none;
}

.tags-input-remove:first-child {
  margin-right: 0.25rem;
}

.tags-input-remove:last-child {
  margin-left: 0.25rem;
}

.tags-input-remove:focus {
  outline: 0;
}

.tags-input-text {
  flex: 1;
  outline: 0;
  padding-top: 0.25rem;
  padding-bottom: 0.25rem;
  margin-left: 0.5rem;
  margin-bottom: 0.25rem;
  min-width: 10rem;
}
</style>
