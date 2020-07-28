<template>
  <div class="top-filter-nav-wrap">
    <div class="filter-elements">
      <form>
        <jtSelect
          class="form-el"
          :list="users"
          :dropName="'dropdown'"
          :showSearch="true"
          :disableD2="disableD1"
          :selectAllID="'selectAll'"
          :dropdownText="'No user selected'"
          @emitChecked="checkFilters"
        />
        <jtSelect
          class="form-el"
          :list="actions"
          :dropName="'dropdown2'"
          :showSearch="false"
          :disableD2="disableD2"
          :selectAllID="'selectAll2'"
          :dropdownText="'No actions selected'"
        />
        <div class="filter-field-wrap">
          <input
            class="select-user-el"
            name="filter_res"
            placeholder="Filter results.."
            v-model="filterText"
            :disabled="filterSearchDis"
          />
          <ion-icon
            name="close-outline"
            class="reset-search"
            v-if="filterText.length > 0"
            @click="resetFilter"
          ></ion-icon>
        </div>
        <button
          type="submit"
          :class="searchBtnDis ? 'search-btn btn-disabled' : 'search-btn'"
          @click="searchFunc"
          :disabled="searchBtnDis"
        >Search Now</button>
      </form>
    </div>
  </div>
</template>

<script>
import jtSelect from "@/components/core/jtSelect.vue";

export default {
  name: "TopFilterNav",
  components: {
    jtSelect,
  },
  data() {
    return {
      users: [
        { name: "zena.huels@gmail.com", id: 500 },
        { name: "welch.lauren@gmail.com", id: 501 },
        { name: "tillman.marisa@cole.com", id: 502 },
        { name: "mariela.lesch@gmail.com", id: 503 },
        { name: "abshire.bertrand@hotmail.com", id: 504 },
        { name: "bledner@hotmail.com", id: 505 },
        { name: "skreiger@jacobs.biz", id: 506 },
        { name: "dbrakus@yahoo.com", id: 507 },
        { name: "tyra.heidenreich@powlowski.com", id: 508 },
        { name: "vwehner@tremblay.com", id: 509 },
        { name: "kessler.eugene@gmail.com", id: 510 },
        { name: "murray.spencer@wisozk.info", id: 511 },
        { name: "toby63@welch.com", id: 512 },
        { name: "rashawn51@yahoo.com", id: 513 },
        { name: "kelsi.crona@crona.net", id: 514 },
        { name: "keebler.monty@mann.com", id: 515 },
        { name: "blanda.rhett@gaylord.com", id: 516 },
        { name: "lebsack.kristy@hotmail.com", id: 517 },
        { name: "bridget33@schuster.com", id: 518 },
        { name: "herzog.maymie@wehner.com", id: 519 },
        { name: "ashleigh10@hotmail.com", id: 520 },
        { name: "weber.sister@yahoo.com", id: 521 },
        { name: "ipfeffer@hotmail.com", id: 522 },
        { name: "derek60@hotmail.com", id: 523 },
        { name: "west.jude@weber.info", id: 524 },
        { name: "eschneider@hintz.biz", id: 525 },
        { name: "evalyn52@goodwin.biz", id: 526 },
        { name: "barrett.auer@wilderman.com", id: 527 },
        { name: "lehner.dayton@yahoo.com", id: 528 },
        { name: "prohaska.britney@hansen.com", id: 529 },
        { name: "christiana59@huels.com", id: 530 },
        { name: "jgerhold@yahoo.com", id: 531 },
        { name: "santino63@bashirian.com", id: 532 },
        { name: "kennith.buckridge@gmail.com", id: 533 },
        { name: "zgoodwin@hotmail.com", id: 534 },
        { name: "jaquan.stark@hotmail.com", id: 535 },
        { name: "raynor.jules@brown.org", id: 536 },
        { name: "curt.johnson@wisozk.com", id: 537 },
        { name: "felton96@wisoky.com", id: 538 },
        { name: "michelle24@hammes.com", id: 539 },
        { name: "nkoelpin@bernhard.com", id: 540 },
        { name: "araceli.goyette@yahoo.com", id: 541 },
        { name: "hrutherford@gmail.com", id: 542 },
        { name: "qschiller@denesik.com", id: 543 },
        { name: "rico.mayer@yahoo.com", id: 544 },
        { name: "amari90@hotmail.com", id: 545 },
        { name: "bframi@gmail.com", id: 546 },
        { name: "fadel.kendall@ward.org", id: 547 },
        { name: "rafael.upton@bayer.info", id: 548 },
      ],
      actions: [
        { name: "Create Client", id: 600 },
        { name: "Create User", id: 601 },
        { name: "Edit Client", id: 602 },
        { name: "Edit User", id: 603 },
        { name: "Change Profile Info", id: 604 },
        { name: "Delete User", id: 605 },
        { name: "Delete Client", id: 606 },
        { name: "Deactivate User", id: 607 },
        { name: "Deactivate Client", id: 608 },
        { name: "Activate User", id: 609 },
        { name: "Activate Client", id: 610 },
        { name: "Log In", id: 611 },
        { name: "Bulk Activate", id: 612 },
        { name: "Bulk Deactivate", id: 613 },
        { name: "Bulk Delete", id: 614 },
        { name: "Log In as User", id: 615 },
        { name: "Log Out As User", id: 616 },
        { name: "Change Password", id: 617 },
        { name: "Initiate Password Reset", id: 618 },
        { name: "Simple Search", id: 619 },
        { name: "Advanced Search", id: 620 },
        { name: "Export to PST", id: 621 },
        { name: "Export to EML", id: 622 },
        { name: "Export to PDF", id: 623 },
        { name: "Download Email", id: 624 },
        { name: "Download Email Attachment", id: 625 },
        { name: "Restore Email", id: 626 },
        { name: "Forward Email", id: 627 },
        { name: "Reply to Email", id: 628 },
        { name: "Reply to All", id: 629 },
        { name: "Ingest Imported Files", id: 630 },
        { name: "Bulk Export Emails as PDF", id: 631 },
        { name: "Bulk Export Emails as EML", id: 632 },
        { name: "Bulk Export Emails as PST", id: 633 },
        { name: "Export All as PDF", id: 634 },
        { name: "Export All as EML", id: 635 },
        { name: "Export All as PST", id: 636 },
        { name: "Bulk Download Emails", id: 637 },
        { name: "Bulk Restore Emails", id: 638 },
        { name: "Bulk Forward Emails", id: 639 },
        { name: "Create Personal Tag", id: 640 },
        { name: "Create Legal Hold Tag", id: 641 },
        { name: "Create Retention Tag", id: 642 },
        { name: "Edit Personal Tag", id: 643 },
        { name: "Edit Legal Hold Tag", id: 644 },
        { name: "Edit Retention Tag", id: 645 },
        { name: "Delete Personal Tag", id: 646 },
        { name: "Delete Legal Hold Tag", id: 647 },
        { name: "Delete Retention Tag", id: 648 },
        { name: "Assign Personal Tag", id: 649 },
        { name: "Assign Legal Hold Tag", id: 650 },
        { name: "Remove Legal Hold Tag", id: 651 },
        { name: "Remove Personal Tag", id: 652 },
        { name: "Bulk Remove Personal Tag", id: 653 },
        { name: "Bulk Remove Legal Hold Tag", id: 654 },
        { name: "Save Simple Search", id: 655 },
        { name: "Save Advanced Search", id: 656 },
        { name: "Delete Saved Search", id: 657 },
        { name: "Delete Recent Simple Search", id: 658 },
        { name: "Delete Recent Advanced Search", id: 659 },
      ],
      filterText: "",
      searchBtnDis: false,
      disableD2: true,
      disableD1: false,
      filterSearchDis: false
    };
  },
  methods: {
    resetFilter() {
      this.filterText = "";
    },
    searchFunc() {
      this.searchBtnDis = true;
      this.disableD1 = true;
      this.disableD2 = true;
      this.filterSearchDis = true;
    },
    checkFilters(payload) {
      if (payload.length < 1) {
        this.disableD2 = true;
      } else {
        this.disableD2 = false;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.top-filter-nav-wrap {
  background-color: #fff;
  border-top: 1px solid #cfcfcf;
  width: 100%;
  height: 70px;
  display: flex;
  align-items: center;
  margin-top: 5px;
  z-index: 10;
  .filter-elements {
    padding: 20px;
    form {
      display: flex;
      .form-el:nth-child(1) {
        margin: 0;
      }
      .form-el {
        margin: 0 15px;
      }
    }
  }
}

.select-user-el {
  border: 1.5px solid #9b9b9b;
  border-radius: 4px;
  outline: none;
  height: 18px;
  width: 250px;
  padding: 10px;
  &:focus {
    border: 1.5px solid #00a88d;
  }
}

.search-btn {
  background-color: #00a88d;
  border: none;
  border-radius: 4px;
  color: #fff;
  cursor: pointer;
  font-size: 14px;
  font-weight: 600;
  outline: none;
  margin: 0 15px;
  width: 115px;
  transition: all 0.2s ease-in-out;
  &:hover {
    background-color: darken(#00a88d, 3%);
  }
}
.btn-disabled {
  opacity: 0.4;
  cursor: not-allowed;
}

.filter-field-wrap {
  position: relative;
  width: 250px;
  input {
    width: 225px;
  }
  .reset-search {
    position: absolute;
    right: 3%;
    top: 30%;
    cursor: pointer;
    &:hover {
      color: #00a88d;
    }
  }
}
</style>