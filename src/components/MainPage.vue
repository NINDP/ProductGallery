<script setup>
import { ref, computed } from 'vue';

let elements = [
    {
        category_name: "PRINT",
        img_path: "print_business_1.png"
    },
    {
        category_name: "PRINT",
        img_path: "print_business_2.png"
    },
    {
        category_name: "PRINT",
        img_path: "print_business_4.png"
    },
    {
        category_name: "WEB DESIGN",
        img_path: "web_desing_1.png"
    },
    {
        category_name: "WEB DESIGN",
        img_path: "web_desing_2.png"
    },
    {
        category_name: "WEB DESIGN",
        img_path: "web_desing_3.png"
    },
    {
        category_name: "PRINT",
        img_path: "print_business_3.png"
    },
    {
        category_name: "WEB DESIGN",
        img_path: "web_desing_4.png"
    },
    {
        category_name: "LOGO",
        img_path: "logo_1.png"
    },
    {
        category_name: "MOTION",
        img_path: "motion_1.png"
    },
    {
        category_name: "MOTION",
        img_path: "motion_2.png"
    },
    {
        category_name: "MOTION",
        img_path: "motion_3.png"
    },
    {
        category_name: "LOGO",
        img_path: "logo_2.png"
    },
    {
        category_name: "LOGO",
        img_path: "logo_3.png"
    },
    {
        category_name: "MOTION",
        img_path: "motion_4.png"
    },
    {
        category_name: "LOGO",
        img_path: "logo_4.png"
    },   
    {
        category_name: "MOTION",
        img_path: "motion_5.png"
    },
    {
        category_name: "LOGO",
        img_path: "logo_5.png"
    },
    {
        category_name: "PRINT",
        img_path: "print_business_5.png"
    },
    {
        category_name: "LOGO",
        img_path: "logo_6.png"
    },
]

let selectedCategory = ref('ALL')

let getUniqueCategories = computed(() => {
    let categories = elements.map(element => element.category_name);
    return categories.filter((category, index) => categories.indexOf(category) === index)
})

let getImagesForCategory = computed(() => {
    if (selectedCategory.value === "ALL") {
        return elements;
    }

    return elements.filter(element => element.category_name == selectedCategory.value);
})

</script>

<template>
<section class="text-center">
    <h1 class="font-bold text-3xl pt-[40px] pb-[10px]">THE PRODUCT GALLERY</h1>
    <p class="text-gray-500 pb-[10px]">awesome products prepared with creative ideas and great design</p>
    <div class="flex justify-center items-center gap-[5px] pb-[40px]">
        <img class="w-[8px] opacity-20" src="/ромб.png" alt="">
        <img class="w-[15px] opacity-20" src="/ромб.png" alt="">
        <img class="w-[8px] opacity-20" src="/ромб.png" alt="">
    </div>
    <div class="flex justify-center text-[15px] font-semibold gap-[50px]">
        <p @click="selectedCategory = 'ALL'" class="cursor-pointer focus:underline" :class="{ active: selectedCategory == 'ALL' }">ALL</p>
        <p class="cursor-pointer" :class="{ active: selectedCategory == element }" v-for="element in getUniqueCategories" :key="element" @click="selectedCategory = element">
            {{ element }}
        </p>
    </div>
    <div class="flex justify-start flex-wrap py-[40px] px-[200px] gap-[15px]">
        <img class="w-[440px] h-[300px]" v-for="element in getImagesForCategory" alt="haha" :key="element" :src="element.img_path"/>
    </div>
</section>
</template>

<style>
.active {
    text-decoration: underline;
    text-decoration-color: green;
    text-decoration-thickness: 2px;
}
</style>
