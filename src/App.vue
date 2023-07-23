<template>
    <VApp id="messagebook">
        <VAppBar>
            <VAppBarNavIcon @click="drawer = !drawer" />

            <VToolbarTitle> {{ TITLE }} </VToolbarTitle>

            <VBtn
                icon
                color="red-darken-1"
                href="https://drive.google.com/file/d/1IHoDgXQjkL2J1T0RKDNB5d_creweUapL/view?usp=drive_link"
                target="_blank"
            >
                <VIcon icon="mdi-file-pdf-box" />
            </VBtn>
        </VAppBar>

        <VNavigationDrawer v-model="drawer">
            <VList
                :items="index"
                item-value="page"
                @click:select="setScroll($event)"
                color="primary"
            />
        </VNavigationDrawer>

        <VMain>
            <VRow no-gutters>
                <VCol
                    v-for="(_, index) in pages"
                    :key="index"
                    :id="index + 1"
                    cols="12"
                    md="6"
                >
                    <VImg
                        :src="`./book/LIA_MESSAGE_BOOK_${(index + 1)
                            .toString()
                            .padStart(3, 0)}.webp`"
                    />
                </VCol>
            </VRow>
        </VMain>

        <!-- <VSnackbar v-model="snackbar" :timeout="2000" rounded="pill"></VSnackbar> -->
    </VApp>
</template>

<script setup>
import { ref } from "vue";

const TITLE = "July, Julia, LIA";

const snackbar = ref(false);

const drawer = ref(false);
const MAX_PAGE = 214;
const pages = new Array(MAX_PAGE);

const setScroll = (page) => {
    document.getElementById(page.id).scrollIntoView(true);
};

const index = [
    {
        title: TITLE,
        page: 1,
    },
    {
        title: "리아의 ENFJ 모먼트",
        page: 5,
    },
    {
        title: "아니 그게...",
        page: 19,
    },
    {
        title: "믿지의 일상",
        page: 35,
    },
    {
        title: "리아의 웃음 스펙트럼",
        page: 71,
    },
    {
        title: "믿지 취향 월드컵",
        page: 87,
    },
    {
        title: "리아의 성장일기",
        page: 113,
    },
    {
        title: "22-23 솔로/커버곡 리뷰",
        page: 127,
    },
    {
        title: "200문 200답",
        page: 141,
    },
    {
        title: "22-23 리아 로드맵",
        page: 177,
    },
];
</script>

<style>
html * {
    font-family: "Pretendard", sans-serif;
}
</style>
