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
      class="tags-input"
      slot-scope="{ tags, removeTag, addTag, inputAttrs, inputEvents }"
    >
      <input
        type="text"
        class="tags-input-text"
        placeholder="New Tag"
        v-bind="inputAttrs"
        v-on="inputEvents"
      />
      <button class="tags-input-tag-add" @click="addTag()">Add</button>
      <ul>
        <li class="tags-input-tag-list" v-for="tag in tags" :key="tag">
          <span class="tags-input-tag">{{ tag }}</span>
          <span
            ><a href="#" class="tags-input-remove" @click="removeTag(tag)"
              >Remove</a
            ></span
          >
        </li>
      </ul>
    </div>
  </renderless-tags-input>
</template>

<script>
import renderlessTagsInput from "@/components/renderless/renderless_tags_input.vue";
export default {
  name: "tagInputAddButton",
  components: {
    renderlessTagsInput,
  },
  props: ["value"],
};
</script>

<style lang="css" scoped>
.tags-input {
  text-align: left;
  background-color: #eff;
  border: 1px solid #ccc;
  border-width: 1px;
  border-radius: 0.25rem;
  padding-left: 0.5rem;
  padding-right: 1rem;
  padding-top: 0.5rem;
  padding-bottom: 0.25rem;
}

.tags-input-tag-list {
  text-align: left;
  margin: 0;
  padding: 0;
}

.tags-input-tag {
  line-height: 1;
  font-size: 1.2rem;
  user-select: none;
  padding: 0.25rem;
  margin-right: 0.5rem;
  margin-bottom: 0.25rem;
  font-family: "Courier New", Courier, monospace;
  font-style: oblique;
  font-weight: bold;
}

.tags-input-tag:last-of-type {
  margin-right: 0;
}

.tags-input-remove {
  color: red;
  font-size: 0.825rem;
  line-height: 1;
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
  outline: 0;
  padding-top: 0.25rem;
  padding-bottom: 0.25rem;
  margin-left: 0.5rem;
  margin-bottom: 0.25rem;
  min-width: 10rem;
}

.tags-input-tag-add {
  margin-left: 1rem;
  background-color: blue;
  color: #fff;
  padding: 0.25rem 1rem;
  border-radius: 5px;
  outline: 0;
  font-weight: bold;
}
</style>
