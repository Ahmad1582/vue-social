<template>
  <div
    v-if="isSettingVisible"
    id="setting-sm"
    tabindex="-1"
    aria-hidden="true"
    class="overflow-y-auto overflow-x-hidden fixed top-0 right-0 left-0 z-50 justify-center items-center w-full md:inset-0 h-[calc(100%-1rem)] max-h-full"
  >
    <div class="relative p-4 w-full max-w-md max-h-full">
      <div class="relative bg-white rounded-lg shadow dark:bg-gray-700">
        <div
          class="flex items-center justify-between p-4 md:p-5 border-b rounded-t dark:border-gray-600"
        >
          <h3 class="text-lg font-semibold text-gray-900 dark:text-white">
            Setting
          </h3>
          <button
            type="button"
            class="text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm h-8 w-8 ms-auto inline-flex justify-center items-center dark:hover:bg-gray-600 dark:hover:text-white"
            @click="closeModal"
          >
            <svg
              class="w-3 h-3"
              aria-hidden="true"
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 14 14"
            >
              <path
                stroke="currentColor"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="m1 1 6 6m0 0 6 6M7 7l6-6M7 7l-6 6"
              />
            </svg>
            <span class="sr-only">Close modal</span>
          </button>
        </div>
        <div class="p-4 md:p-5">
          <ul class="space-y-4 mb-4">
            <li @click="showInfo">
              <input
                type="radio"
                id="job-1"
                name="job"
                value="job-1"
                class="hidden peer"
                required
              />
              <label
                for="job-1"
                class="inline-flex items-center justify-between w-full p-5 text-gray-900 bg-white border border-gray-200 rounded-lg cursor-pointer dark:hover:text-gray-300 dark:border-gray-500 dark:peer-checked:text-blue-500 peer-checked:border-blue-600 peer-checked:text-blue-600 hover:text-gray-900 hover:bg-gray-100 dark:text-white dark:bg-gray-600 dark:hover:bg-gray-500"
              >
                <div class="block">
                  <div class="w-full text-lg font-semibold">
                    support & More Info
                  </div>
                  <div class="w-full text-gray-500 dark:text-gray-400">
                    How I can Help You
                  </div>
                </div>
                <svg
                  class="w-4 h-4 ms-3 rtl:rotate-180 text-gray-500 dark:text-gray-400"
                  aria-hidden="true"
                  xmlns="http://www.w3.org/2000/svg"
                  fill="none"
                  viewBox="0 0 14 10"
                >
                  <path
                    stroke="currentColor"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M1 5h12m0 0L9 1m4 4L9 9"
                  />
                </svg>
              </label>
            </li>
            <SupportInfo v-if="isShowInfo"></SupportInfo>
            <li @click="showLogout">
              <input
                type="radio"
                id="job-2"
                name="job"
                value="job-2"
                class="hidden peer"
              />
              <label
                for="job-2"
                class="inline-flex items-center justify-between w-full p-5 text-gray-900 bg-white border border-gray-200 rounded-lg cursor-pointer dark:hover:text-gray-300 dark:border-gray-500 dark:peer-checked:text-blue-500 peer-checked:border-blue-600 peer-checked:text-blue-600 hover:text-gray-900 hover:bg-gray-100 dark:text-white dark:bg-gray-600 dark:hover:bg-gray-500"
              >
                <div class="block">
                  <div class="w-full text-lg font-semibold">Logout</div>
                  <div class="w-full text-gray-500 dark:text-gray-400">
                    Exit or switch account
                  </div>
                </div>
                <svg
                  class="w-4 h-4 ms-3 rtl:rotate-180 text-gray-500 dark:text-gray-400"
                  aria-hidden="true"
                  xmlns="http://www.w3.org/2000/svg"
                  fill="none"
                  viewBox="0 0 14 10"
                >
                  <path
                    stroke="currentColor"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M1 5h12m0 0L9 1m4 4L9 9"
                  />
                </svg>
              </label>
            </li>
            <LogOut v-if="isShowLogout"></LogOut>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, defineEmits, defineProps } from "vue";
import SupportInfo from "../settingprofile/SupportInfo.vue";
import LogOut from "../settingprofile/LogOut.vue";

const isShowInfo = ref(false);
const isShowLogout = ref(false);

const props = defineProps({
  isSettingVisible: Boolean,
});
const emit = defineEmits(["close"]);

const closeModal = () => {
  emit("close");
};

function showInfo() {
  isShowInfo.value = true;
}
function showLogout() {
  isShowLogout.value = true;
}
</script>

<style></style>
