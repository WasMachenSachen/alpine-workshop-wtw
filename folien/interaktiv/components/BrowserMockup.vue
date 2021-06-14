<template>
  <div class="max-w-2xl mx-auto my-10">
    <div
      class="
        w-full
        h-11
        relative
        rounded-t-lg
        bg-blue-900
        flex
        overflow-hidden
        justify-start
        items-center
        space-x-1.5
        px-2
      "
    >
      <div class="absolute w-full h-full inset-0 bg-black opacity-50"></div>
      <span
        class="relative w-3 h-3 border-2 rounded-full border-red-400"
      ></span>
      <span
        class="relative w-3 h-3 border-2 rounded-full border-yellow-400"
      ></span>
      <span
        class="relative w-3 h-3 border-2 rounded-full border-green-400"
      ></span>
    </div>
    <div
      class="
        relative
        bg-blue-200
        border-t-0
        w-full
        h-96
        border-t border-blue-900
      "
    ><slot/>
    </div>
  </div>
</template>
