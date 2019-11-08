<template>
  <form class="mb-4">
    <div class="mb-4">
      <label class="block text-gray-700 text-sm font-bold mb-2">
        Username
      </label>
      <input
        class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
        type="text" placeholder="Username">
    </div>
    <div class="mb-6">
      <label class="block text-gray-700 text-sm font-bold mb-2">
        Password
      </label>
      <input
        class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
        type="password" placeholder="******************">
    </div>
    <div class="flex items-center justify-between">
      <button
        class="bg-teal-500 hover:bg-teal-600 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
        type="button">
        Sign In
      </button>
      <a class="inline-block align-baseline font-bold text-sm text-teal-500 hover:text-teal-800" href="#">
        Forgot Password?
      </a>
    </div>
  </form>
</template>
