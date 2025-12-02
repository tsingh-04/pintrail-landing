<script> 
  export const title = "";
  import logo from '/pintrails-logo.png';
</script>

<header class="hero">
  <div class="title-row">
    <h1>PinTrails</h1>
    <img src={logo} alt="PinTrails logo" class="logo" />
  </div>
</header>

<style>
  header {
    width: 100%;
    text-align: center;
    padding: 24px 0 8px 0;
  }

  .title-row {
    display: inline-flex;         
    align-items: center;
    gap: 1rem;                    
  }

   h1 {
    margin: 0;           
  }

  .logo {
    width: 64px;               
    height: 64px;
  }
  
</style>