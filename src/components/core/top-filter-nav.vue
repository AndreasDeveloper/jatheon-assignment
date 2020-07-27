<template>
  <div class="top-filter-nav-wrap">
    <div class="filter-elements">
      <form>
        <jtSelect class="form-el" :list="users" :dropName="'dropdown'" />
        <jtSelect class="form-el" :list="actions" :dropName="'dropdown2'" />
        <!-- <SearchSelect class="form-el" :list="users" :searchInField="true" :placeholder="'No user selected'" :fieldName="'selectUser'" /> -->
        <!-- <SearchSelect class="form-el" :list="actions" :searchInField="false" :placeholder="'No actions selected'" :fieldName="'selectAction'" /> -->
        <input class="select-user-el" name="filter_res" placeholder="Filter results.." />
        <button type="submit" class="search-btn">Search Now</button>
      </form>
    </div>
  </div>
</template>

<script>
import SearchSelect from "@/components/core/search-select.vue";
import jtSelect from "@/components/core/jtSelect.vue";

export default {
  name: "TopFilterNav",
  components: {
    SearchSelect,
    jtSelect
  },
  data() {
    return {
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
      ],
      actions: [
        'Create Client',
        'Create User',
        'Edit Client',
        'Edit User',
        'Change Profile Info',
        'Delete User',
        'Delete Client',
        'Deactivate User',
        'Deactivate Client',
        'Activate User',
        'Activate Client',
        'Log In',
        'Bulk Activate',
        'Bulk Deactivate',
        'Bulk Delete',
        'Log In as User',
        'Log Out As User',
        'Change Password',
        'Initiate Password Reset',
        'Simple Search',
        'Advanced Search',
        'Export to PST',
        'Export to EML',
        'Export to PDF',
        'Download Email',
        'Download Email Attachment',
        'Restore Email',
        'Forward Email',
        'Reply to Email',
        'Reply to All',
        'Ingest Imported Files',
        'Bulk Export Emails as PDF',
        'Bulk Export Emails as EML',
        'Bulk Export Emails as PST',
        'Export All as PDF',
        'Export All as EML',
        'Export All as PST',
        'Bulk Download Emails',
        'Bulk Restore Emails',
        'Bulk Forward Emails',
        'Create Personal Tag',
        'Create Legal Hold Tag',
        'Create Retention Tag',
        'Edit Personal Tag',
        'Edit Legal Hold Tag',
        'Edit Retention Tag',
        'Delete Personal Tag',
        'Delete Legal Hold Tag',
        'Delete Retention Tag',
        'Assign Personal Tag',
        'Assign Legal Hold Tag',
        'Remove Legal Hold Tag',
        'Remove Personal Tag',
        'Bulk Remove Personal Tag',
        'Bulk Remove Legal Hold Tag',
        'Save Simple Search',
        'Save Advanced Search',
        'Delete Saved Search',
        'Delete Recent Simple Search',
        'Delete Recent Advanced Search'
      ]
    };
  },
};
</script>

<style lang="scss" scoped>
.top-filter-nav-wrap {
  background-color: #fff;
  border-top: 1px solid #CFCFCF;
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
    border: 1.5px solid #9B9B9B;
    border-radius: 4px;
    outline: none;
    height: 18px;
    width: 250px;
    padding: 10px;
  }

.search-btn {
    background-color: #00A88D;
    border: none;
    border-radius: 4px;
    color: #fff;
    cursor: pointer;
    font-size: 14px;
    font-weight: 600;
    outline: none;
    margin: 0 15px;
    width: 115px;
}
</style>