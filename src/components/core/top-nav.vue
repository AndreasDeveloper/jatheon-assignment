<template>
    <div class="top-nav-wrap">
        <div class="top-elements">
            <form>
                <ion-icon name="search" class="search-icon"></ion-icon>
                <input type="text" name="search" placeholder="Search for a word or phrase" class="search-field">
            </form>
            <div class="user-data">
                <span class="user-initials"><strong>MA</strong></span>
                <ion-icon name="chevron-down-outline" class="dd-icon"></ion-icon>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TopNav'
}
</script>

<style lang="scss" scoped>
.top-nav-wrap {
    background-color: #fff;
    width: 100%;
    height: 60px;
    .top-elements {
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 20px;
        // Form
        form {
            position: relative;
            .search-icon {
                color: #9B9B9B;
                font-size: 18px;
                position: absolute;
                top: 25%;
                left: 1.5%;
            }
            .search-field {
                background-color: #F4F4F4;
                border: none;
                border-radius: 4px;
                width: 500px;
                height: 38px;
                padding-left: 35px;
                outline: none;
                &::placeholder {
                    color: #9B9B9B;
                }
            }
        }
        // User Initials / Dropdown
        .user-data {
            display: flex;
            align-items: center;
            .user-initials {
                background-color: #F4F4F4;
                border-radius: 100%;
                color: #9B9B9B;
                font-size: 13px;
                line-height: 2.5;
                text-align: center;
                height: 35px;
                width: 35px;
            }
            .dd-icon {
                color: #9B9B9B;
                font-size: 18px;
                margin-left: 5px;
            }
        }
    }
}
</style>