<template>
  <nav class="navbar navbar-expand-md navbar-light bg-secondary">
    <div class="container">
      <a class="navbar-brand" href="#">
        <img
          src="~/assets/img/books.png"
          alt="Logo"
          width="50"
          height="50"
          class="align-text-top"
        />
      </a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div id="navbarSupportedContent" class="collapse navbar-collapse">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="/">Home</a>
          </li>
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="#">We Books</a>
          </li>
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="/about"
              >About</a
            >
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
