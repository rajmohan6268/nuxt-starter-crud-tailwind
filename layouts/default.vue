
<template>
  <div class="bg-gray-900 font-sans leading-normal tracking-normal mt-12">
    <!--Nav-->
    <nav class="bg-gray-900 pt-2 md:pt-1 pb-1 px-1 mt-0 h-auto fixed w-full z-20 top-0">
      <div class="flex flex-wrap items-center">
        <div class="flex flex-shrink md:w-1/3 justify-center md:justify-start text-white">
          <a href="#">
            <span class="text-xl pl-2">
              <i class="em em-grinning"></i>
            </span>
          </a>
        </div>

        <div class="flex w-full pt-2 content-end justify-between md:w-1/3 md:justify-end">
          <ul class="list-reset flex justify-between flex-1 md:flex-none items-end">
            <li class="flex-1 md:flex-none md:mr-3">
              <a class="inline-block py-2 px-4 text-white no-underline" href="/test">test</a>
            </li>
            <li class="flex-1 md:flex-none md:mr-3">
              <a
                class="inline-block text-gray-600 no-underline hover:text-gray-200 hover:text-underline py-2 px-4"
                href="/try"
              >try</a>
            </li>
            <li class="flex-1 md:flex-none md:mr-3">
              <div class="relative inline-block"></div>
            </li>
          </ul>
        </div>
      </div>
    </nav>

    <div class="flex flex-col md:flex-row">
      <div
        class="bg-gray-900 shadow-lg h-16 fixed bottom-0 mt-12 md:relative md:h-screen z-10 w-full md:w-48"
      >
        <div
          class="md:mt-12 md:w-48 md:fixed md:left-0 md:top-0 content-center md:content-start text-left justify-between"
        >
          <ul
            class="list-reset flex flex-row md:flex-col py-0 md:py-3 px-1 md:px-2 text-center md:text-left"
          >
            <li>
              <a class="inline-block py-2 px-4 text-white no-underline" href="/">
                <svg
                  width="24"
                  height="24"
                  viewBox="0 0 24 24"
                  fill="none"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <path
                    d="M13.1459 11.0499L12.9716 9.05752L15.3462 8.84977C14.4471 7.98322 13.2242 7.4503 11.8769 7.4503C9.11547 7.4503 6.87689 9.68888 6.87689 12.4503C6.87689 15.2117 9.11547 17.4503 11.8769 17.4503C13.6977 17.4503 15.2911 16.4771 16.1654 15.0224L18.1682 15.5231C17.0301 17.8487 14.6405 19.4503 11.8769 19.4503C8.0109 19.4503 4.87689 16.3163 4.87689 12.4503C4.87689 8.58431 8.0109 5.4503 11.8769 5.4503C13.8233 5.4503 15.5842 6.24474 16.853 7.52706L16.6078 4.72412L18.6002 4.5498L19.1231 10.527L13.1459 11.0499Z"
                    fill="currentColor"
                  />
                </svg>
              </a>
            </li>
            <li class="mr-3 flex-1">
              <a
                href="/"
                class="block py-1 md:py-3 pl-1 align-middle text-white no-underline hover:text-white border-b-2 border-gray-800 hover:border-pink-500"
              >
                <i class="fas fa-tasks pr-0 md:pr-3"></i>
                <span
                  class="pb-1 md:pb-0 text-xs md:text-base text-gray-600 md:text-gray-400 block md:inline-block"
                >Tasks</span>
              </a>
            </li>
            <li class="mr-3 flex-1">
              <a
                href="#"
                class="block py-1 md:py-3 pl-1 align-middle text-white no-underline hover:text-white border-b-2 border-gray-800 hover:border-purple-500"
              >
                <i class="fa fa-envelope pr-0 md:pr-3"></i>
                <span
                  class="pb-1 md:pb-0 text-xs md:text-base text-gray-600 md:text-gray-400 block md:inline-block"
                >crud</span>
              </a>
            </li>

            <li class="mr-3 flex-1">
              <a
                href="#"
                class="block py-1 md:py-3 pl-1 align-middle text-white no-underline hover:text-white border-b-2 border-gray-800 hover:border-purple-500"
              >
                <i class="fa fa-envelope pr-0 md:pr-3"></i>
                <span
                  class="pb-1 md:pb-0 text-xs md:text-base text-gray-600 md:text-gray-400 block md:inline-block"
                >get</span>
              </a>
            </li>
            <li class="mr-3 flex-1">
              <a
                href="#"
                class="block py-1 md:py-3 pl-1 align-middle text-white no-underline hover:text-white border-gray-800 border-b-2 hover:border-blue-600"
              >
                <i class="fas fa-chart-area pr-0 md:pr-3 text-blue-600"></i>
                <span
                  class="pb-1 md:pb-0 text-xs md:text-base text-white md:text-white block md:inline-block"
                >post</span>
              </a>
            </li>
            <li class="mr-3 flex-1">
              <a
                href="#"
                class="block py-1 md:py-3 pl-0 md:pl-1 align-middle text-white no-underline border-b-2 border-gray-800 hover:border-red-500"
              >
                <i class="fa fa-wallet pr-0 md:pr-3"></i>
                <span
                  class="pb-1 md:pb-0 text-xs md:text-base text-gray-600 md:text-gray-400 block md:inline-block"
                >put</span>
              </a>
            </li>
            <li class="mr-3 flex-1">
              <a
                href="#"
                class="block py-1 md:py-3 pl-1 align-middle text-white no-underline hover:text-white border-b-2 border-gray-800 hover:border-purple-500"
              >
                <i class="fa fa-envelope pr-0 md:pr-3"></i>
                <span
                  class="pb-1 md:pb-0 text-xs md:text-base text-gray-600 md:text-gray-400 block md:inline-block"
                >delete</span>
              </a>
            </li>
          </ul>
        </div>
      </div>

      <div class="main-content flex-1 bg-gray-100 mt-12 md:mt-2 pb-24 md:pb-5">
        <div class="bg-blue-800 p-2 shadow text-xl text-white">
          <h3 class="font-bold pl-2">Nuxt crud</h3>
        </div>
        <Nuxt />
      </div>
    </div>
  </div>
</template>
