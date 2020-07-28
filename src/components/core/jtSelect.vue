<template>
  <div class="cs-wrap">
    <div
      class="checkbox-select__trigger"
      :class="{ isActive: activeTrigger, disabledField: disableD2 }"
      @click="showDropdown"
    >
      <span class="checkbox-select__title" v-if="checkedFilters.length < 1">{{ dropdownText }}</span>
      <span class="checkbox-select__title" v-else-if="allSelected">{{ field1Text }}</span>
      <span
        class="checkbox-select__title"
        v-else-if="checkedFilters.length > 0 && allSelected === false"
      >{{ checkedFilters[checkedFilters.length - 1] }}</span>
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 129 129">
        <path
          d="M121.3 34.6c-1.6-1.6-4.2-1.6-5.8 0l-51 51.1-51.1-51.1c-1.6-1.6-4.2-1.6-5.8 0-1.6 1.6-1.6 4.2 0 5.8l53.9 53.9c.8.8 1.8 1.2 2.9 1.2 1 0 2.1-.4 2.9-1.2l53.9-53.9c1.7-1.6 1.7-4.2.1-5.8z"
        />
      </svg>
    </div>
    <div :id="dropName" class="checkbox-select__dropdown">
      <div class="checkbox-select__search-wrapp" v-if="showSearch">
        <ion-icon name="search" class="search-icon"></ion-icon>
        <input type="text" placeholder="Search for a user.." v-model="search" @keyup="hideSA = true" />
        <ion-icon
          name="close-outline"
          class="reset-search"
          v-if="search.length > 0"
          @click="resetSearch"
        ></ion-icon>
      </div>
      <div :class="!showSearch ? 'checkbox-select__col marginTop' : 'checkbox-select__col'">
        <div class="checkbox-select__select-all" v-if="!hideSA || search.length === 0">
          <ion-icon name="checkmark-outline" class="check-icon" @click="selectAll($event)"></ion-icon>
          <input type="checkbox" :id="selectAllID" @click="selectAll($event)" :value="selectAllID" />
          <label :for="selectAllID">{{selectAllText}}</label>
        </div>
      </div>
      <ul class="checkbox-select__filters-wrapp">
        <li v-for="(filter, index) in filteredList" :key="index">
          <div class="checkbox-select__check-wrapp">
            <ion-icon name="checkmark-outline" class="check-icon" @click="checkCheckbox($event)"></ion-icon>
            <input
              :id="filter.id"
              class="conditions-check"
              v-model="checkedFilters"
              :value="filter.name"
              type="checkbox"
              @change="emitChecked"
            />
            <label :for="filter.id">{{filter.name}}</label>
          </div>
        </li>
        <span class="no-res" v-if="filteredList.length === 0">No Results Found</span>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "jtSelect",
  props: {
    list: {
      type: Array,
    },
    dropName: {
      type: String,
    },
    showSearch: {
      type: Boolean
    },
    disableD2: {
      type: Boolean
    },
    selectAllID: {
      type: String
    },
    dropdownText: {
      type: String
    }
  },
  data() {
    return {
      search: "",
      checkedFilters: [],
      allSelected: false,
      selectAllText: "Select All",
      activeTrigger: false,
      dropdown: false,
      field1Text: "",
      hideSA: false
    };
  },
  computed: {
    filteredList() {
      return this.$props.list.filter((item) => {
        return item.name.toLowerCase().includes(this.search.toLowerCase());
      });
    },
  },
  methods: {
    selectAll: function (e) {
      if (e.path[4].children[1].checked === false) {
        e.path[4].children[1].checked = true;
      } else {
        e.path[4].children[1].checked = false;
      }
      this.allSelected = !this.allSelected;
      this.checkedFilters = [];
      this.selectAllText =
        this.selectAllText == "Select All" ? "Clear All" : "Select All";
      if (this.allSelected) {
        if (this.$props.dropName === 'dropdown2') {
          this.field1Text = 'All Actions';
        } else {
          this.field1Text = "All Users";
        }
        for (let i = 0; i < this.$props.list.length; i++) {
          this.checkedFilters.push(this.$props.list[i].name.toString());
        }
      }
      this.$emit('emitChecked', this.checkedFilters);
    },
    showDropdown: function () {
      if (this.dropdown == false && this.$props.disableD2 === false) {
        this.dropdown = true;
        this.activeTrigger = true;
        TweenMax.fromTo(
          `#${this.$props.dropName}`,
          0.55,
          {
            autoAlpha: 0,
            y: -10,
          },
          {
            autoAlpha: 1,
            y: 0,
            ease: Power2.easeOut,
          }
        );
      } else {
        this.dropdown = false;
        this.activeTrigger = false;
        TweenMax.to(`#${this.$props.dropName}`, 0.2, {
          autoAlpha: 0,
          y: -10,
          ease: Power2.easeOut,
        });
      }
    },
    resetSearch() {
      this.search = "";
    },
    emitChecked() {
      this.$emit('emitChecked', this.checkedFilters);
    },
    checkCheckbox(e) {
      let checked = e.path[4].children[1].checked;
      let index = this.checkedFilters.indexOf(e.path[4].children[1].value);
      if (checked === true) {
        checked = false;
        this.checkedFilters.splice(index, 1);
      } else {
        this.checkedFilters.push(e.path[4].children[1].value);
        checked = true;
      }
      this.$emit('emitChecked', this.checkedFilters);
    }
  },
};
</script>

<style lang="scss" scoped>
@import "../../styles/global/dropdown.scss";

.marginTop {
  margin-top: 10px;
}

.isActive {
  border: 1.5px solid #00A88D;
}
.no-res {
  color: #9B9B9B;
  font-size: 14px;
  padding-left: 10px;
}

.disabledField {
  background: #F4F4F4;
  border: 1.5px solid #CFCFCF;
}
</style>