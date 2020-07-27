<template>
  <div class="top-nav-wrap">
    <div class="top-elements">
      <form>
        <ion-icon name="search" class="search-icon"></ion-icon>
        <input
          type="text"
          name="search"
          placeholder="Search for a word or phrase"
          class="search-field"
        />
      </form>
      <div class="user-data">
        <span id="uinitials" class="user-initials" @click="openDropdown">
          <strong>MA</strong>
        </span>
        <ion-icon name="chevron-up-outline" class="dd-icon" v-if="openD"></ion-icon>
        <ion-icon name="chevron-down-outline" class="dd-icon" v-else></ion-icon>
        <div id="userD" class="dropdown" v-if="openD">
          <span class="d-title">Administrator</span>
          <span class="user-email">mike.andrew@jatheon.com</span>
          <span class="team-name">Jatheon Technologies</span>
          <ul>
            <li>
              <a href="#">Account Settings</a>
            </li>
            <li>
              <a href="#">Company Settings</a>
            </li>
            <li>
              <a href="#">Help Center</a>
            </li>
            <!-- <li>
              <a href="#">Keyboard Shortcuts</a>
            </li> -->
            <li>
              <a href="#">Log Out</a>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TopNav",
  data() {
    return {
      openD: false,
    };
  },
  methods: {
    openDropdown() {
      this.openD = !this.openD;
      document.querySelector("#uinitials").classList.toggle("backColor");
    },
  },
};
</script>

<style lang="scss" scoped>
.top-nav-wrap {
  background-color: #fff;
  width: 100%;
  height: 60px;
  z-index: 15;
  .top-elements {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 10px 20px;
    // Form
    form {
      position: relative;
      .search-icon {
        color: #9b9b9b;
        font-size: 18px;
        position: absolute;
        top: 25%;
        left: 1.5%;
      }
      .search-field {
        background-color: #f4f4f4;
        border: none;
        border-radius: 4px;
        width: 500px;
        height: 38px;
        padding-left: 35px;
        outline: none;
        &::placeholder {
          color: #9b9b9b;
        }
      }
    }
    // User Initials / Dropdown
    .user-data {
      display: flex;
      align-items: center;
      position: relative;
      .user-initials {
        background-color: #f4f4f4;
        border-radius: 100%;
        color: #9b9b9b;
        cursor: pointer;
        font-size: 13px;
        line-height: 2.5;
        text-align: center;
        height: 35px;
        width: 35px;
      }
      .dd-icon {
        color: #9b9b9b;
        cursor: pointer;
        font-size: 18px;
        margin-left: 5px;
      }
    }
  }
}

// Account Dropdown
.dropdown {
  position: absolute;
  background-color: #fff;
  padding: 10px;
  border: 1px solid #cfcfcf;
  border-radius: 4px;
  box-shadow: 0px 3px 4px 0px rgba(#000000, 0.1);
  width: 230px;
  right: 0%;
  top: 110%;
  text-align: left;
  display: flex;
  flex-direction: column;
  .d-title {
    color: #9b9b9b;
    font-size: 11px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 1px;
  }
  .user-email {
    color: #3e4543;
    font-size: 14px;
    font-weight: 600;
    margin-top: 5px;
  }
  .team-name {
    color: #3e4543;
    font-size: 14px;
    margin-top: 5px;
  }
  ul {
    border-top: 1px solid #cfcfcf;
    list-style: none;
    text-align: left;
    padding: 10px 0px 0px 0px;
    margin-bottom: 0px;
    li {
      cursor: pointer;
      font-size: 14px;
      margin: 10px 0;
      a {
        color: #3e4543;
        text-decoration: none;
        transition: all 0.2s ease-in-out;
        &:hover {
          color: #00a88d;
        }
      }
    }
    li:nth-child(5) {
      margin: 0;
    }
  }
}

.backColor {
  background-color: #00a88c38 !important;
  color: #00a88d !important;
}
</style>