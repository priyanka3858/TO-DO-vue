<script>
export default {
  data() {
    return {
      messages: [],
      msg: "",
    };
  },
  methods: {
    addItem(event) {
      event.preventDefault();
      if (this.msg !== "") {
        this.messages.push({ value: this.msg, checked: false });
        this.msg = "";
      }
    },
    deleteItem(event, index) {
      event.preventDefault();
      this.messages.splice(index, 1);
    },
    toggleCheckbox(event, index) {
      if (event.target.checked) {
        this.messages[index].checked = true;
      } else {
        this.messages[index].checked = false;
      }
    },
  },
};
</script>

<template>
  <div class="bg-white">
    <div class="">
      <div
        class="mx-auto max-w-md px-4 sm:max-w-3xl sm:px-6 lg:max-w-7xl lg:px-8"
      >
        <div
          class="rounded-2xl px-6 py-10 bg-indigo-600 overflow-hidden shadow-xl sm:px-4 sm:py-6"
        >
          <div class="">
            <div class="sm:text-center">
              <h2
                class="text-3xl font-extrabold text-white tracking-tight sm:text-4xl"
              >
                To Do List
              </h2>
            </div>
            <form action="#" class="mt-12 sm:mx-auto sm:max-w-lg sm:flex">
              <div class="min-w-0 flex-1">
                <label for="cta-email" class="sr-only">Email address</label>
                <input
                  id="cta-email"
                  type="text"
                  v-model="msg"
                  class="block w-full border border-transparent rounded-md px-5 py-3 text-base text-gray-900 placeholder-gray-500 shadow-sm focus:outline-none focus:border-transparent focus:ring-2 focus:ring-white focus:ring-offset-2 focus:ring-offset-indigo-600"
                  placeholder="Enter item"
                />
              </div>
              <div class="mt-4 sm:mt-0 sm:ml-3">
                <button
                  type="submit"
                  @click="(event) => addItem(event)"
                  class="block w-full rounded-md border border-transparent px-5 py-3 bg-indigo-500 text-base font-medium text-white shadow hover:bg-indigo-400 focus:outline-none focus:ring-2 focus:ring-white focus:ring-offset-2 focus:ring-offset-indigo-600 sm:px-10"
                >
                  Add
                </button>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div class="max-w-xl mx-auto flow-root mt-6">
    <ul role="list" class="-my-5 divide-y divide-gray-200">
      <li v-for="(item, index) in messages" :key="index" class="py-4">
        <div class="flex items-center space-x-4">
          <div class="ml-3 flex items-center h-5">
            <input
              type="checkbox"
              @click="toggleCheckbox($event, index)"
              class="focus:ring-indigo-500 h-4 w-4 accent-indigo-600 text-indigo-600 border-gray-300 rounded"
            />
          </div>
          <div class="flex-1 min-w-0">
            <p
              :class="{ 'line-through': item.checked === true }"
              class="text-lg font-medium text-gray-900 truncate"
            >
              {{ item.value }}
            </p>
          </div>
          <div>
            <button
              @click="(event) => deleteItem(event, index)"
              class="inline-flex items-center shadow-sm px-2.5 py-0.5 border border-gray-300 text-sm leading-5 font-medium rounded-full text-gray-700 bg-white hover:bg-gray-50"
            >
              Delete
            </button>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<style scoped></style>
