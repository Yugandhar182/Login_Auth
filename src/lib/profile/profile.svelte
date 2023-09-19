<script>
    import { goto } from '$app/navigation';
    import { auth } from '$lib/firebase/firebase.js';
    
    let showModal = false;
  
    function openModal() {
      showModal = true;
    }
  
    function closeModal() {
      showModal = false;
    }

    function handleLogout() {
    // Display a confirmation dialog
    const confirmLogout = window.confirm("Are you sure you want to logout?");
    
    if (confirmLogout) {
      // User confirmed, proceed with logout
      // You can use your Firebase auth instance to sign the user out
      // For example:
      auth.signOut().then(() => {
        // Handle successful logout, e.g., navigate to the /information page
        console.log("User logged out");
        goto('/'); // Navigate to the /information route
      }).catch((error) => {
        // Handle logout error, if any
        console.error("Logout error:", error);
      });
    }
  }

  
    function Businessprofile() {
      goto('/businessprofile');
    }
  </script>
  
  <img class="imag" src="https://i.stack.imgur.com/YQu5k.png" alt="Click me" on:click={openModal} />
  
  {#if showModal}
    <div class="modal">
      <div class="modal-content">
        <span class="close" style="margin-left: 100px;" on:click={closeModal}>&times;</span>
        
       
        <h3 class="h3"  style="color: blue; cursor: pointer;" on:click={Businessprofile}>Business Profile</h3>
     <hr>
        <h4 class="h4"  style="color: red; cursor: pointer;" on:click={handleLogout}>Logout</h4>
      </div>
    </div>
  {/if}
  
  <style>
   .imag {
    position: absolute;
    top: 10px;
    right: 10px;
    height: 50px;
  }
  
    .h3{
        margin-right: 80px;
    }
    .h4{
        margin-right: 140px;
        margin-top: 60px;
    }
  
    .modal {
      display: block;
      position: fixed;
      top: 0;
      margin-left: 10px;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.5);
      z-index: 999;
      text-align: center;
    }
  
    .modal-content {
      background-color:white;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      padding: 20px;
      border-radius: 5px;
      height: 150px;
      width: 300px;
      margin-left: 600px;
      margin-top: -200px;
    }
  
    .close {
      position: absolute;
      top: 0;
      margin-right: 0;
      padding: 10px;
      cursor: pointer;
    }
  </style>
  