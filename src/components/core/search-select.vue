<template>
  <div class="jt-select">
    <input type="text" name="select-user" placeholder="No user selected" id="user-s" class="select-user-el" @click="openDropdown" />
    <ion-icon name="chevron-down-outline" class="dd-icon" v-if="openD" @click="openDropdown"></ion-icon>
    <ion-icon name="chevron-up-outline" class="dd-icon" v-else @click="openDropdown"></ion-icon>
    <div id="dd1" class="dropdown" v-if="openD">
      <form>
        <ion-icon name="search" class="search-icon"></ion-icon>
        <input
          type="text"
          name="search"
          placeholder="Search for a user.."
          class="search-field"
        />
        </form>
        <div class="result-users">
            <div class="result-users__el" @click="selectAll">
                <input type="checkbox" name="select_all">
                <label for="select_all">Select All</label>
            </div>
            <div class="result-users__el" v-for="(user, i) in users" :key="i">
                <input type="checkbox" :name="user" :checked="checkA">
                <label :for="user">{{ user }}</label>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SearchSelect",
  data() {
    return {
      openD: false,
      checkA: false,
      users: [
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
        "rafael.upton@bayer.info"
      ]
    };
  },
  methods: {
    openDropdown() {
        this.openD = !this.openD;
        document.querySelector('#user-s').classList.toggle('borderChange');
    },
    selectAll() {
        this.checkA = !this.checkA;
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
    border: 1px solid #9B9B9B;
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
        label {
            margin-left: 5px;
        }
    }
  }
}

// Toggle state for button styles
.borderChange {
    border: 1px solid #00A88D !important;
}
</style>