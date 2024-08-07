<script>
  import { onMount } from 'svelte';

  /**
   * Boolean to track the state of the navbar (open/closed).
   * @type {boolean}
   */
  let navbarOpen = false;
  
  const toggleNavbar = () => {
    navbarOpen = !navbarOpen;
  };
  
  onMount(() => {
    const handleOutsideClick = (event) => {
      if (!event.target.closest('#navbar-dropdown') && !event.target.closest('.navbar-toggle')) {
        navbarOpen = false;
      }
    };

    document.addEventListener('click', handleOutsideClick);
    return () => document.removeEventListener('click', handleOutsideClick);
  });
</script>

<header class="header">
  <div class="header-content">
    <a href="/">
      <img src="/online-shop.png" alt="SwiftCart Logo" class="brand-logo">
      <h1 class="header-title">SwiftCart</h1>
    </a>
    <div class="header-right">
      <h3 class="wishlist">
        <a href="#" class="wishlist-btn">
          <span class="wishlist-icon">♡</span>
          <span class="wishlist-text">Wishlist</span>
        </a>
      </h3>
      <div class="cart">
        <a href="#">
          <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="cart-icon">
            <path stroke-linecap="round" stroke-linejoin="round" d="M2.25 3h1.386c.51 0 .955.343 1.087.835l.383 1.437M7.5 14.25a3 3 0 00-3 3h15.75m-12.75-3h11.218c1.121-2.3 2.1-4.684 2.924-7.138a60.114 60.114 0 00-16.536-1.84M7.5 14.25L5.106 5.272M6 20.25a.75.75 0 11-1.5 0 .75.75 0 011.5 0zm12.75 0a.75.75 0 11-1.5 0 .75.75 0 011.5 0z"></path>
          </svg>
        </a>
        <span class="cart-badge">2</span>
      </div>
      <div class="login"><a href="/login">Login</a></div>
    </div>
    <button
      on:click={toggleNavbar}
      type="button"
      class="navbar-toggle"
      aria-controls="navbar-dropdown"
      aria-expanded={navbarOpen}
    >
      <span class="sr-only">Open main menu</span>
      <svg class="toggle-icon" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 17 14">
        <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M1 1h15M1 7h15M1 13h15" />
      </svg>
    </button>
  </div>
  
  <div id="navbar-dropdown" class={`navbar-dropdown ${navbarOpen ? '' : 'hidden'}`}>
    <ul class="navbar-menu">
      <li><a href="#" class="menu-item">Wishlist</a></li>
      <li>
        <a href="#" class="menu-item">
          <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="cart-icon">
            <path stroke-linecap="round" stroke-linejoin="round" d="M2.25 3h1.386c.51 0 .955.343 1.087.835l.383 1.437M7.5 14.25a3 3 0 00-3 3h15.75m-12.75-3h11.218c1.121-2.3 2.1-4.684 2.924-7.138a60.114 60.114 0 00-16.536-1.84M7.5 14.25L5.106 5.272M6 20.25a.75.75 0 11-1.5 0 .75.75 0 011.5 0zm12.75 0a.75.75 0 11-1.5 0 .75.75 0 011.5 0z"></path>
          </svg>
          <span class="cart-badge">2</span>
        </a>
      </li>
      <li><a href="/login" class="menu-item">Login</a></li>
    </ul>
  </div>
</header>

<style>
  .header {
    background-color: #767c89;
    color: #fff;
    padding: 1rem;
    top: 0;
    z-index: 50;
  }

  .header-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
    max-width: 100%;
    margin: 0 auto;
    position: relative;
  }

  .brand-logo {
    height: 50px;
    margin-right: 0;
    top: 30%;
    left: 2%;
    position: absolute;
  }

  .header-title {
    text-align: left;
    margin-left: 40%;
    color: white;
  }

  .header-right {
    display: flex;
    align-items: right;
    gap: 1rem;
  }

  .wishlist, .cart, .login {
    display: flex;
    align-items: center;
  }

  .wishlist-btn, .menu-item {
    color: #fff;
    text-decoration: none;
    padding: 0.5rem;
    border-radius: 0.25rem;
  }

  .wishlist-btn:hover, .menu-item:hover {
    background-color: #555;
  }

  .cart-icon {
    height: 24px;
    width: 24px;
    color: white;
  }

  .login a{
    color: white;
  }

  .cart-badge {
    background-color: #e53935;
    color: #fff;
    border-radius: 50%;
    width: 20px;
    height: 20px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 0.75rem;
    margin-left: -10px;
    margin-top: -10px;
  }

  .navbar-toggle {
    display: none;
    background: none;
    border: none;
    color: #fff;
    font-size: 1.5rem;
    cursor: pointer;
  }

  .navbar-dropdown {
    display: none;
    background-color: #333;
    padding: 1rem;
    border-radius: 0.25rem;
    position: absolute;
    top: 100%;
    right: 0;
    width: 200px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  .navbar-dropdown.hidden {
    display: none;
  }

  .navbar-menu {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  .menu-item {
    color: #fff;
    text-decoration: none;
    display: block;
    padding: 0.5rem;
  }

  .menu-item:hover {
    background-color: #555;
  }

  @media (max-width: 768px) {
    .navbar-toggle {
      display: block;
    }

    .header-right {
      display: none;
    }
  }
</style>
