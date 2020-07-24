<template>
    <div class="top-filter-nav-wrap">
        <div class="filter-elements">
            <form>
                <SearchSelect />
            </form>
        </div>
    </div>
</template>

<script>
import SearchSelect from '@/components/core/search-select.vue';

export default {
    name: 'TopFilterNav',
    components: {
        SearchSelect
    }
}
</script>

<style lang="scss" scoped>
.top-filter-nav-wrap {
    background-color: #fff;
    width: 100%;
    height: 70px;
    display: flex;
    align-items: center;
    .filter-elements {
        padding: 20px;
    }
}
</style>