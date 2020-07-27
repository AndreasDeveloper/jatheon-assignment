<template>
  <div class="jt-select">
    <input type="text" :name="fieldName" :placeholder="placeholder" id="user-s" class="select-user-el" @click="openDropdown" v-if="searchInField" :value="checkedMails[checkedMails.length - 1]" />
    <input type="text" :name="fieldName" :placeholder="placeholder" id="user-s" class="select-user-el" @click="openDropdown" v-else />
    <ion-icon name="chevron-down-outline" class="dd-icon" v-if="openD" @click="openDropdown"></ion-icon>
    <ion-icon name="chevron-up-outline" class="dd-icon" v-else @click="openDropdown"></ion-icon>
    <div id="dd1" class="dropdown" v-if="openD">
      <form v-if="searchInField">
        <ion-icon name="search" class="search-icon"></ion-icon>
        <input
          type="text"
          name="search"
          placeholder="Search for a user.."
          class="search-field"
          v-model="filter"
          @keyup="filterMails"
        />
        </form>
        <div class="result-users">
            <div class="result-users__el" @click="selectAll">
                <input type="checkbox" name="select_all">
                <label for="select_all">Select All</label>
            </div>
            <div class="result-users__el" v-for="(el, i) in list" :key="i">
                <input type="checkbox" class="checkboxes1" :name="el" :checked="checkA" @click="handleCheck($event)">
                <label :for="el">{{ el }}</label>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SearchSelect",
  props: {
    list: {
      type: Array
    },
    searchInField: {
      type: Boolean
    },
    placeholder: {
      type: String
    },
    fieldName: {
      type: String
    }
  },
  data() {
    return {
      openD: false,
      checkA: false,
      filter: '',
      mails: [],
      checkedMails: [],
      checkedActions: []
    };
  },
  watch: {
    list: {
      handler(val, oldVal) {
        if (val.length < 50) {
          this.mails = val;
        }
      },
      immediate: true
    }
  },
  methods: {
    openDropdown() {
        this.openD = !this.openD;
        document.querySelector('#user-s').classList.toggle('borderChange');
    },
    selectAll() {
        this.checkA = !this.checkA;
    },
    filterMails() {
      console.log(this.field)
      for (let i = 0; i < this.mails.length; i++) {
        if (this.filter.split('') === this.mails[i].split('')) {
          console.log(this.mails[i])
        }
      }
    },
    handleCheck(e) {
      this.checkedMails.push(e.target.name);
      console.log(this.checkedMails)
    }
  }
};
</script>

<style lang="scss" scoped>
.jt-select {
  position: relative;
  input,
  .dd-icon {
    cursor: pointer;
  }
  .select-user-el {
    border: 1.5px solid #9B9B9B;
    border-radius: 4px;
    outline: none;
    height: 18px;
    width: 250px;
    padding: 10px;
  }
  .dd-icon {
    position: absolute;
    right: 3%;
    top: 30%;
  }
}

// Dropdown
.dropdown {
  position: absolute;
  background-color: #fff;
  padding: 12px;
  border: 1px solid #CFCFCF;
  border-radius: 4px;
  box-shadow: 0px 3px 4px 0px rgba(#000000, 0.1);
  width: 90%;
  // Form
  form {
    position: relative;
    text-align: left;
    .search-icon {
      color: #9b9b9b;
      font-size: 18px;
      position: absolute;
      top: 13%;
      left: 3%;
    }
    .search-field {
      background-color: #f4f4f4;
      border: none;
      border-radius: 4px;
      width: 200px;
      height: 30px;
      padding-left: 35px;
      outline: none;
      margin-bottom: 15px;
      &::placeholder {
        color: #9b9b9b;
      }
    }
  }
  .result-users {
      max-height: 350px;
      overflow-y: scroll;
    &__el {
        display: flex;
        align-items: center;
        overflow-x: hidden;
        input:checked {
          color: #00A88D;
          background: #00A88D;
        }
        label {
            cursor: pointer;
            margin-left: 5px;
            text-align: left;
            transition: all .2s ease-in-out;
            &:hover {
              color: #00A88D;
            }
        }
    }
  }
}

// Toggle state for button styles
.borderChange {
    border: 1.5px solid #00A88D !important;
}
</style>