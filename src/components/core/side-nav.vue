<template>
    <div class="side-nav-wrap">
        <img src="../../assets/logo.png" alt="Jatheon Logo" class="logo-main">
        <div class="nav-elements">
            <ul>
                <li>
                    <img src="../../assets/icondashboard.svg" alt="Dashboard Icon">
                    <span><strong>Audit</strong></span>
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
                span {
                    margin-left: 12px;
                }
            }
        }
    }
}
</style>