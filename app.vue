<template>
 <div><MainSection/></div>
</template>
<script lang="ts">

export default {
  // Define properties with initial values


  mounted() {
    // Get values from URL query parameters
    const clientCode = this.$route.query.clientcode? this.$route.query.clientcode as string : "GZ10219";
    const clientName =this.$route.query.clientname? this.$route.query.clientname as string : "RAMANADHAN";
    const clientemail=this.$route.query.clientemail? this.$route.query.clientemail as string : "eswaran@gwcindia.in";
    // Do something with clientCode and clientName
    // this.clientCode = "GZ10219";
    // this.clientName = "RAJA ESWARAN";
    // this.clientemail=   "eswaran@gwcindia.in";
    localStorage.setItem('clientemail', JSON.stringify(clientCode));
 localStorage.setItem('clientName', JSON.stringify(clientName));
 localStorage.setItem('clientCode', JSON.stringify(clientemail));
 
    this.$router.push('/homePage');
  

    console.log('Client Code:', clientCode);
    console.log('Client Name:', clientName);
    console.log('Client Name:', clientemail);
  }


}
</script>
