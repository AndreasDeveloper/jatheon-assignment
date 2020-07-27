<template>
  <div class="cs-wrap">
    <div
      class="checkbox-select__trigger"
      :class="{ isActive: activeTrigger }"
      @click="showDropdown"
    >
      <span class="checkbox-select__title" v-if="checkedFilters.length < 1">No user selected</span>
      <span class="checkbox-select__title" v-else>{{ checkedFilters[checkedFilters.length - 1] }}</span>
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 129 129">
        <path
          d="M121.3 34.6c-1.6-1.6-4.2-1.6-5.8 0l-51 51.1-51.1-51.1c-1.6-1.6-4.2-1.6-5.8 0-1.6 1.6-1.6 4.2 0 5.8l53.9 53.9c.8.8 1.8 1.2 2.9 1.2 1 0 2.1-.4 2.9-1.2l53.9-53.9c1.7-1.6 1.7-4.2.1-5.8z"
        />
      </svg>
    </div>
    <div id="dropdown" class="checkbox-select__dropdown" :class="{ activeSearch: showLoader }">
      <div class="checkbox-select__search-wrapp">
        <ion-icon name="search" class="search-icon"></ion-icon>
        <input
          type="text"
          @focus="showLoader = true"
          @blur="showLoader = false"
          placeholder="Search for a user.."
          v-model="search"
        />
        <ion-icon name="close-outline" class="reset-search" v-if="search.length > 1" @click="resetSearch"></ion-icon>
      </div>
      <div class="checkbox-select__col">
        <div class="checkbox-select__select-all" v-model="selectAll">
          <label for="selectAll">{{selectAllText}}</label>
          <input type="checkbox" id="selectAll" @click="selectAll" v-model="allSelected" />
        </div>
      </div>
      <ul class="checkbox-select__filters-wrapp">
        <li v-for="(filter, index) in filteredList" :key="index">
          <div class="checkbox-select__check-wrapp">
            <ion-icon name="checkmark-outline" class="check-icon"></ion-icon>
            <input
              :id="index"
              class="conditions-check"
              v-model="checkedFilters"
              :value="filter"
              type="checkbox"
            />
            <label :for="index">{{filter}}</label>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "jtSelect",
  data() {
    return {
      filters: [
        "zena.huels@gmail.com",
        "welch.lauren@gmail.com",
        "tillman.marisa@cole.com",
        "mariela.lesch@gmail.com",
        "abshire.bertrand@hotmail.com",
        "bledner@hotmail.com",
        "skreiger@jacobs.biz",
        "dbrakus@yahoo.com",
        "tyra.heidenreich@powlowski.com",
        "vwehner@tremblay.com",
        "kessler.eugene@gmail.com",
        "murray.spencer@wisozk.info",
        "toby63@welch.com",
        "rashawn51@yahoo.com",
        "kelsi.crona@crona.net",
        "keebler.monty@mann.com",
        "blanda.rhett@gaylord.com",
        "lebsack.kristy@hotmail.com",
        "bridget33@schuster.com",
        "herzog.maymie@wehner.com",
        "ashleigh10@hotmail.com",
        "weber.sister@yahoo.com",
        "ipfeffer@hotmail.com",
        "derek60@hotmail.com",
        "west.jude@weber.info",
        "eschneider@hintz.biz",
        "evalyn52@goodwin.biz",
        "barrett.auer@wilderman.com",
        "lehner.dayton@yahoo.com",
        "prohaska.britney@hansen.com",
        "christiana59@huels.com",
        "jgerhold@yahoo.com",
        "santino63@bashirian.com",
        "kennith.buckridge@gmail.com",
        "zgoodwin@hotmail.com",
        "jaquan.stark@hotmail.com",
        "raynor.jules@brown.org",
        "curt.johnson@wisozk.com",
        "felton96@wisoky.com",
        "michelle24@hammes.com",
        "nkoelpin@bernhard.com",
        "araceli.goyette@yahoo.com",
        "hrutherford@gmail.com",
        "qschiller@denesik.com",
        "rico.mayer@yahoo.com",
        "amari90@hotmail.com",
        "bframi@gmail.com",
        "fadel.kendall@ward.org",
        "rafael.upton@bayer.info",
      ],
      search: "",
      checkedFilters: [],
      allSelected: false,
      selectAllText: "Select All",
      activeTrigger: false,
      dropdown: false,
      showLoader: false,
    };
  },
  computed: {
    filteredList() {
      return this.filters.filter((item) => {
        return item.toLowerCase().includes(this.search.toLowerCase());
      });
    },
  },
  methods: {
    selectAll: function () {
      this.checkedFilters = [];
      this.selectAllText =
      this.selectAllText == "Select All" ? "Clear All" : "Select All";
      if (this.allSelected) {
        for (filter in this.filters) {
          this.checkedFilters.push(this.filters[filter].toString());
        }
      }
    },
    showDropdown: function () {
      if (this.dropdown == false) {
        this.dropdown = true;
        this.activeTrigger = true;
        TweenMax.fromTo(
          "#dropdown",
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
        TweenMax.to("#dropdown", 0.2, {
          autoAlpha: 0,
          y: -10,
          ease: Power2.easeOut,
        });
      }
    },
    resetSearch() {
      this.search = '';
    },
  },
};
</script>

<style lang="scss" scoped>
.cs-wrap {
  position: relative;
  width: 250px;
}

body {
  height: 100vh;
  padding: 0 15px;
  background: rgb(143, 36, 237);
  background: -moz-linear-gradient(
    -45deg,
    rgba(143, 36, 237, 1) 20%,
    rgba(143, 36, 237, 1) 20%,
    rgba(143, 36, 237, 1) 22%,
    rgba(143, 36, 237, 1) 25%,
    rgba(16, 124, 179, 1) 100%
  );
  background: -webkit-linear-gradient(
    -45deg,
    rgba(143, 36, 237, 1) 20%,
    rgba(143, 36, 237, 1) 20%,
    rgba(143, 36, 237, 1) 22%,
    rgba(143, 36, 237, 1) 25%,
    rgba(16, 124, 179, 1) 100%
  );
  background: linear-gradient(
    135deg,
    rgba(143, 36, 237, 1) 20%,
    rgba(143, 36, 237, 1) 20%,
    rgba(143, 36, 237, 1) 22%,
    rgba(143, 36, 237, 1) 25%,
    rgba(16, 124, 179, 1) 100%
  );
  filter: progid:DXImageTransform.Microsoft.gradient(
      startColorstr="#8f24ed",
      endColorstr="#107cb3",
      GradientType=1
    );
  display: flex;
  align-items: center;
  justify-content: center;
  @media only screen and (max-width: 600px) {
    display: block;
  }
}
* {
  outline: none;
  -webkit-tap-highlight-color: rgba(255, 255, 255, 0);
}

*,
:after,
:before {
  box-sizing: border-box;
}

textarea,
input {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  border-radius: 0;
}

.checkbox-select {
  position: relative;
  max-width: 440px;
  width: 100%;
  @media only screen and (max-width: 600px) {
    margin: 100px auto 0;
  }
  &__trigger {
    border-radius: 4px;
    border: 1.5px solid #9b9b9b;
    background-color: #fff;
    position: relative;
    z-index: 1;
    height: 41px;
    display: flex;
    align-items: center;
    cursor: pointer;
    padding: 0 25px;
    padding-left: 0;
    transition: all 0.4s ease;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    text-align: left;
    padding-left: 10px;
    @media only screen and (max-width: 600px) {
      padding: 0 15px;
      height: 70px;
    }
    &.isActive {
      svg {
        transform: rotate(-180deg);
      }
    }
    svg {
      width: 13px;
      height: 13px;
      transition: all 0.4s ease;
      margin-right: -15px;
      @media only screen and (max-width: 600px) {
        width: 22px;
      }
    }
  }
  &__title {
    font-size: 12px;
    flex: 1;
    padding-right: 25px;
    letter-spacing: 1px;
    @media only screen and (max-width: 600px) {
      font-size: 19px;
    }
  }
  &__dropdown {
    opacity: 0;
    visibility: hidden;
    background: #fff
      url("http://res.cloudinary.com/dnhvfgp9c/image/upload/v1521734636/bcg-pattern.png")
      repeat;
    position: absolute;
    left: 0;
    right: 0;
    box-shadow: 0px 3px 4px 0px rgba(#000000, 0.1);
    border-radius: 0 0 8px 8px;
    overflow: hidden;
    width: 100%;
    margin-top: 10px;
    &.activeSearch {
      &:after {
        opacity: 1;
      }
    }
  }
  &__search-wrapp {
    position: relative;
    padding: 10px 10px 5px;
    @media only screen and (max-width: 600px) {
      padding: 10px 15px 5px;
    }
    .search-icon {
      color: #9b9b9b;
      font-size: 16px;
      position: absolute;
      top: 35%;
      left: 7%;
    }
    input {
      width: 100%;
      height: 30px;
      border: none;
      border-radius: 4px;
      font-size: 14px;
      background-color: #f4f4f4;
      padding-left: 30px;
    }
    .reset-search {
      cursor: pointer;
      position: absolute;
      top: 35%;
      right: 12%;
    }
    ::-webkit-input-placeholder {
      /* Chrome/Opera/Safari */
      color: #b8b8b8;
      opacity: 1;
    }
    ::-moz-placeholder {
      /* Firefox 19+ */
      color: #b8b8b8;
      opacity: 1;
    }
    :-ms-input-placeholder {
      /* IE 10+ */
      color: #b8b8b8;
      opacity: 1;
    }
    :-moz-placeholder {
      /* Firefox 18- */
      color: #b8b8b8;
      opacity: 1;
    }
  }
  &__col {
    display: flex;
    font-size: 12px;
    padding: 0 25px;
    justify-content: space-between;
    text-transform: uppercase;
    @media only screen and (max-width: 600px) {
      padding: 0 15px;
    }
  }
  &__select-all {
    label {
      cursor: pointer;
    }
    input {
      display: none;
    }
  }
  &__filters-wrapp {
    list-style: none;
    text-align: left;
    padding-left: 0;
    margin-top: 5px;
    height: 157px;
    overflow-y: auto;
    overflow-x: hidden;
  }

  &__check-wrapp {
    position: relative;
    padding: 0 10px;
    margin-bottom: 5px;
    @media only screen and (max-width: 600px) {
      padding: 0 15px;
    }
    .check-icon {
      color: #fff;
      position: absolute;
      top: 25%;
      z-index: 999;
      cursor: pointer;
    }
    input[type="checkbox"] {
      display: none;

      & + label {
        position: relative;
        cursor: pointer;
        font-size: 13px;
        line-height: 17px;
        padding-left: 28px;
        display: inline-block;
        -webkit-touch-callout: none;
        -webkit-user-select: none;
        -khtml-user-select: none;
        -moz-user-select: none;
        -ms-user-select: none;
        user-select: none;
        transition: padding 0.25s ease;
        &:hover {
          color: #00a88d;
          &:after {
            border: 1px solid #00a88d;
          }
        }
        &:after {
          border: solid 1px #9b9b9b;
          border-radius: 4px;
          content: "";
          width: 18px;
          height: 18px;
          top: 0;
          left: 0;
          position: absolute;
        }
        &:before {
          width: 17.5px;
          height: 17.5px;
          content: "";
          position: absolute;
          top: 0;
          left: 0;
          border-radius: 4px;
          background-color: #00a88d;
          opacity: 0;
          will-change: transform;
          transform: scale(0.5);
          transition: all 0.2s ease;
          .check-icon {
            display: block;
          }
        }
        &:hover {
          padding-left: 32px;
        }
      }
      &:checked {
        & + label {
          &:before {
            opacity: 1;
            transform: scale(1);
          }
        }
      }
    }
  }
}

@keyframes load {
  0% {
    left: -200px;
    width: 20%;
  }
  50% {
    width: 40%;
  }
  70% {
    width: 60%;
  }
  80% {
    left: 50%;
  }
  95% {
    left: 120%;
  }
  100% {
    left: 100%;
  }
}

.link {
  position: absolute;
  left: 0;
  bottom: 0;
  padding: 20px;
  z-index: 9999;
  a {
    display: flex;
    align-items: center;
    text-decoration: none;
    color: #fff;
  }
  .fa {
    font-size: 28px;
    margin-right: 8px;
    color: #fff;
  }
}
</style>