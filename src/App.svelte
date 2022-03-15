<script lang="ts">

  import { ethers } from 'ethers';

  export let address: string = "Address";
  export let private_key: string = "Private Key";

  export function generate() {
    let new_wallet = ethers.Wallet.createRandom()
    address = new_wallet.address;
    private_key = new_wallet.privateKey
  }

</script>

<main>
  <section >  
    <div class="head">
      <h1>Wallet Generator</h1>
    </div>

    <div class="generator-ui">
      <button 
      class="button" 
      on:click={() => navigator.clipboard.writeText(address)}>
      {address === 'Address' ? 'Address' : (address.slice(0,4) + '...' + address.slice(38,42))}
      </button>

      <button 
      class="button" 
      on:click={() => navigator.clipboard.writeText(private_key)}>
      {private_key === 'Private Key' ? 'Private Key' : (private_key.slice(0,4) + '...' + private_key.slice(62,66))}
      </button>
    </div>

    <div class="button-container">
      <button class="generator-button" on:click={generate}>New Wallet</button>
    </div>
  </section>
</main>

<style>
  :global(*) {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    font-family: sans-serif;
  }

  section {
    margin-top: 15%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .generator-ui {
    width: 600px;
    height: 100px;
    background-color: #ff3e00;
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    align-items: center;
    border-radius: 10px;
    margin-top: 10px;
  }

  .button-container {
    width: 600px;
    height: 30px;
    display: flex;
    flex-direction: column;
  }

  .head {
    width: 600px;
    font-size: 30px;
    color: #ff3e00;
  }

  .button {
  -webkit-border-radius: 4;
  -moz-border-radius: 4;
  border-radius: 6px;
  color: #1c1c1c;
  font-size: 20px;
  background: #FBF6F4;
  padding: 10px 20px 10px 20px;
  text-decoration: none;
  border: none;
}

.button:hover {
  background: #c4bfbe;
  text-decoration: none;
}

.generator-button {
  margin-top: 10px;
  border-radius: 10px;
  padding: 10px 20px 10px 20px;
  text-decoration: none;
  font-size: 20px;
  background-color: #D61200;
  color: #FBF6F4;
  border: none;
  font-weight: 600;
}


</style>
