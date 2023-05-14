<script lang="ts">
  interface Certificate {
    _id: string;
    certificatenumber: string;
    certificatereport: number;
    certificationnotlicensed: boolean;
    certificationstatusid: number;
    companyid: number;
    id: number;
    notlicensed: boolean;
    notlicensedmessage: null | string;
    product: string;
    sectorid: number;
    standard: string;
    statusid: number;
    suspended: boolean;
    technicalspecification: null | string;
  }

  let data: Certificate[] = [];

  fetch("http://localhost:8080/api/certificates")
    .then((response) => response.json())
    .then((json: Certificate[]) => {
      data = json;
    });
</script>

<div id="filter-container">
  <h3>Filters</h3>
  <h4>Product</h4>
  <label><input type="checkbox" name="filter1" value="filter1" />Filter 1</label
  ><br />
  <label><input type="checkbox" name="filter2" value="filter2" />Filter 2</label
  ><br />
  <label><input type="checkbox" name="filter3" value="filter3" />Filter 3</label
  ><br />
  <label><input type="checkbox" name="filter4" value="filter4" />Filter 4</label
  ><br />
  <label><input type="checkbox" name="filter5" value="filter5" />Filter 5</label
  ><br />
  <h4>Toepassing</h4>
  <label><input type="checkbox" name="filter6" value="filter6" />Filter 6</label
  ><br />
  <label><input type="checkbox" name="filter7" value="filter7" />Filter 7</label
  ><br />
  <label><input type="checkbox" name="filter8" value="filter8" />Filter 8</label
  ><br />
  <label><input type="checkbox" name="filter9" value="filter9" />Filter 9</label
  ><br />
  <label
    ><input type="checkbox" name="filter10" value="filter10" />Filter 10</label
  ><br />
  <h4>Licentiestatus</h4>
  <label
    ><input
      type="checkbox"
      name="filter11"
      value="filter11"
    />gecertificeerd</label
  ><br />
  <label
    ><input type="checkbox" name="filter12" value="filter12" />geschorst</label
  ><br />
</div>

<div id="certificate-container">
  <div class="tabs">
    <span class="tab active">All Certificates</span>
    <span class="tab">Favorites</span>
  </div>
  {#each data.slice(0, 15) as certificate}
    <div class="cert">
      <p>
        {certificate.product} :
      </p>
      {#if certificate.suspended}
        <svg
          width="22"
          height="21"
          viewBox="0 0 22 21"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M6.825 19.9864L5.375 17.5364L2.625 16.9364C2.375 16.8864 2.175 16.757 2.025 16.5484C1.875 16.3397 1.81667 16.1107 1.85 15.8614L2.125 13.0364L0.25 10.8864C0.0833333 10.703 0 10.4864 0 10.2364C0 9.98637 0.0833333 9.7697 0.25 9.58637L2.125 7.43637L1.85 4.61137C1.81667 4.36137 1.875 4.13203 2.025 3.92337C2.175 3.7147 2.375 3.5857 2.625 3.53637L5.375 2.93637L6.825 0.486367C6.95833 0.269701 7.14167 0.123701 7.375 0.0483674C7.60833 -0.0269659 7.84167 -0.0142993 8.075 0.0863674L10.675 1.18637L13.275 0.0863674C13.5083 -0.0136326 13.7417 -0.0262992 13.975 0.0483674C14.2083 0.123034 14.3917 0.269034 14.525 0.486367L15.975 2.93637L18.725 3.53637C18.975 3.58637 19.175 3.7157 19.325 3.92437C19.475 4.13303 19.5333 4.36203 19.5 4.61137L19.225 7.43637L21.1 9.58637C21.2667 9.7697 21.35 9.98637 21.35 10.2364C21.35 10.4864 21.2667 10.703 21.1 10.8864L19.225 13.0364L19.5 15.8614C19.5333 16.1114 19.475 16.3407 19.325 16.5494C19.175 16.758 18.975 16.887 18.725 16.9364L15.975 17.5364L14.525 19.9864C14.3917 20.203 14.2083 20.349 13.975 20.4244C13.7417 20.4997 13.5083 20.487 13.275 20.3864L10.675 19.2864L8.075 20.3864C7.84167 20.4864 7.60833 20.499 7.375 20.4244C7.14167 20.3497 6.95833 20.2037 6.825 19.9864ZM9.625 10.9364L8.175 9.51137C7.99167 9.32803 7.76233 9.23637 7.487 9.23637C7.21167 9.23637 6.97433 9.33637 6.775 9.53637C6.59167 9.7197 6.5 9.95303 6.5 10.2364C6.5 10.5197 6.59167 10.753 6.775 10.9364L8.925 13.0864C9.125 13.2864 9.35833 13.3864 9.625 13.3864C9.89167 13.3864 10.125 13.2864 10.325 13.0864L14.575 8.83637C14.775 8.63637 14.8707 8.40303 14.862 8.13637C14.8533 7.8697 14.7577 7.63637 14.575 7.43637C14.375 7.23637 14.1373 7.13237 13.862 7.12437C13.5867 7.11637 13.3493 7.21203 13.15 7.41137L9.625 10.9364Z"
            fill="#FEA338"
          />
        </svg>
        <p class="uncertified">geschorst</p>
      {:else}
        <svg
          width="22"
          height="21"
          viewBox="0 0 22 21"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M6.825 19.9864L5.375 17.5364L2.625 16.9364C2.375 16.8864 2.175 16.757 2.025 16.5484C1.875 16.3397 1.81667 16.1107 1.85 15.8614L2.125 13.0364L0.25 10.8864C0.0833333 10.703 0 10.4864 0 10.2364C0 9.98637 0.0833333 9.7697 0.25 9.58637L2.125 7.43637L1.85 4.61137C1.81667 4.36137 1.875 4.13203 2.025 3.92337C2.175 3.7147 2.375 3.5857 2.625 3.53637L5.375 2.93637L6.825 0.486367C6.95833 0.269701 7.14167 0.123701 7.375 0.0483674C7.60833 -0.0269659 7.84167 -0.0142993 8.075 0.0863674L10.675 1.18637L13.275 0.0863674C13.5083 -0.0136326 13.7417 -0.0262992 13.975 0.0483674C14.2083 0.123034 14.3917 0.269034 14.525 0.486367L15.975 2.93637L18.725 3.53637C18.975 3.58637 19.175 3.7157 19.325 3.92437C19.475 4.13303 19.5333 4.36203 19.5 4.61137L19.225 7.43637L21.1 9.58637C21.2667 9.7697 21.35 9.98637 21.35 10.2364C21.35 10.4864 21.2667 10.703 21.1 10.8864L19.225 13.0364L19.5 15.8614C19.5333 16.1114 19.475 16.3407 19.325 16.5494C19.175 16.758 18.975 16.887 18.725 16.9364L15.975 17.5364L14.525 19.9864C14.3917 20.203 14.2083 20.349 13.975 20.4244C13.7417 20.4997 13.5083 20.487 13.275 20.3864L10.675 19.2864L8.075 20.3864C7.84167 20.4864 7.60833 20.499 7.375 20.4244C7.14167 20.3497 6.95833 20.2037 6.825 19.9864ZM9.625 10.9364L8.175 9.51137C7.99167 9.32803 7.76233 9.23637 7.487 9.23637C7.21167 9.23637 6.97433 9.33637 6.775 9.53637C6.59167 9.7197 6.5 9.95303 6.5 10.2364C6.5 10.5197 6.59167 10.753 6.775 10.9364L8.925 13.0864C9.125 13.2864 9.35833 13.3864 9.625 13.3864C9.89167 13.3864 10.125 13.2864 10.325 13.0864L14.575 8.83637C14.775 8.63637 14.8707 8.40303 14.862 8.13637C14.8533 7.8697 14.7577 7.63637 14.575 7.43637C14.375 7.23637 14.1373 7.13237 13.862 7.12437C13.5867 7.11637 13.3493 7.21203 13.15 7.41137L9.625 10.9364Z"
            fill="#4ECB71"
          />
        </svg>
        <p class="certified">gecertificeerd</p>
        <img src="src/assets/unFavourite.svg" alt="favourite button" />
      {/if}
    </div>
  {/each}
</div>

<style lang="scss">
  @import "src/styles/main.scss";
</style>