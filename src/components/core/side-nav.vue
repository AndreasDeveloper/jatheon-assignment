<template>
    <div class="side-nav-wrap">
        <img src="../../assets/logo.png" alt="Jatheon Logo" class="logo-main">
        <div class="nav-elements">
            <ul>
                <li>
                    <img src="../../assets/icondashboard.svg" alt="Dashboard Icon">
                    <span><a href="#"><strong>Audit</strong></a></span>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: 'SideNav'
}
</script>

<style lang="scss" scoped>
.side-nav-wrap {
    background-color: #E1E7E9;
    min-height: 100vh;
    width: 250px;
    .logo-main {
        padding: 20px;
    }
    .nav-elements {
        ul {
            list-style: none;
            float: left;
            li {
                color: #00A88D;
                cursor: pointer;
                display: flex;
                align-items: center;
                img {
                    height: 18px;
                    width: 18px;
                }
                span {
                    font-size: 16px;
                    margin-left: 12px;
                    line-height: 1;
                    a {
                        color: inherit;
                        text-decoration: none;
                    }
                }
            }
        }
    }
}
</style>