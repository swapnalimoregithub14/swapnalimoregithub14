<!DOCTYPE html>
<html>

<head>
  <title>Page not found</title>
  <script type="text/javascript">
    window.isErrorPage = true;
    window.errorCode = '404';
  </script>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta property="og:title" content="Page not found">
  <script src="/scripts/scripts.js" type="module" crossorigin="use-credentials"></script>
  <script type="module">
    import { sampleRUM } from '/scripts/aem.js';

    window.addEventListener('load', () => {
      if (document.referrer) {
        const { origin, pathname } = new URL(document.referrer);
        if (origin === window.location.origin) {
          const backBtn = document.createElement('a');
          backBtn.classList.add('button', 'error-button-back');
          backBtn.href = pathname;
          backBtn.textContent = 'Go back';
          backBtn.title = 'Go back';
          const btnContainer = document.querySelector('.button-container');
          btnContainer.append(backBtn);
        }
      }
      sampleRUM('404', { source: document.referrer, target: window.location.href });
    });
  </script>
  <link rel="stylesheet" href="/styles/styles.css">
  <style>
    main.error {
      min-height: calc(100vh - var(--nav-height));
      display: flex;
      align-items: center;
    }

    main.error .error-number {
      width: 100%;
    }

    main.error .error-number text {
      font-family: var(--fixed-font-family);
    }
  </style>
  <link rel="stylesheet" href="/styles/lazy-styles.css">
</head>

<body>
  <header></header>
  <main class="error">
    <div class="section">
      <svg viewBox="1 0 38 18" class="error-number">
        <text x="0" y="17">404</text>
      </svg>
      <h2 class="error-message">Page Not Found</h2>
      <p class="button-container">
        <a href="/" class="button secondary error-button-home">Go home</a>
      </p>
    </div>
  </main>
  <footer></footer>
</body>

</html>
