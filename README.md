# index.html<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Notificação Avançada Dark</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap');

  /* Reset básico e fonte moderna */
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  body {
    background: linear-gradient(135deg, #0f2027, #203a43, #2c5364);
    color: #e0e0e0;
    font-family: 'Inter', sans-serif;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    padding: 20px;
  }

  /* Contêiner da notificação */
  .notification {
    position: fixed;
    bottom: 32px;
    right: 32px;
    background: rgba(30, 30, 30, 0.85);
    backdrop-filter: blur(12px);
    border-radius: 16px;
    box-shadow:
      0 8px 32px rgba(0, 0, 0, 0.6),
      inset 0 0 0 1px rgba(255, 255, 255, 0.1);
    color: #f1f1f1;
    padding: 24px 32px 24px 24px;
    min-width: 320px;
    max-width: 360px;
    display: flex;
    gap: 16px;
    align-items: center;
    animation: slideInUp 0.5s cubic-bezier(0.4, 0, 0.2, 1);
  }

  @keyframes slideInUp {
    from {
      transform: translateY(100%);
      opacity: 0;
    }
    to {
      transform: translateY(0);
      opacity: 1;
    }
  }

  /* Ícone */
  .notification-icon {
    flex-shrink: 0;
    background: linear-gradient(135deg, #6b5bff, #4dd0e1);
    border-radius: 50%;
    width: 48px;
    height: 48px;
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: 0 4px 12px rgba(77, 208, 225, 0.5);
    transition: transform 0.3s ease;
  }

  .notification-icon svg {
    width: 24px;
    height: 24px;
    fill: white;
  }

  .notification:hover .notification-icon {
    transform: scale(1.15);
  }

  /* Conteúdo da notificação */
  .notification-content {
    flex: 1;
    display: flex;
    flex-direction: column;
    gap: 6px;
  }

  .notification-title {
    font-size: 1.25rem;
    font-weight: 700;
    color: #bb86fc;
    letter-spacing: 0.03em;
  }

  .notification-message {
    font-size: 0.95rem;
    line-height: 1.4;
    color: #cfcfcf;
  }

  /* Botão fechar */
  .close-button {
    background: transparent;
    border: none;
    color: #aaa;
    cursor: pointer;
    font-size: 1.5rem;
    padding: 4px;
    line-height: 1;
    transition: color 0.3s ease;
    flex-shrink: 0;
    align-self: start;
  }

  .close-button:hover,
  .close-button:focus {
    color: #bb86fc;
    outline: none;
  }

  /* Acessibilidade: foco visível */
  .close-button:focus-visible {
    outline: 2px solid #bb86fc;
    outline-offset: 2px;
  }
</style>
</head>
<body>

<div class="notification" role="alert" aria-live="assertive" aria-atomic="true">
  <div class="notification-icon" aria-hidden="true">
    <!-- Ícone avançado SVG material design -->
    <svg viewBox="0 0 24 24" aria-label="Informação">
      <path d="M11 17h2v-6h-2v6zm1-14C6.48 3 2 7.48 2 13s4.48 10 10 10 10-4.48 10-10S17.52 3 12 3zm0 18c-4.42 0-8-3.58-8-8 0-4.41 3.58-8 8-8 4.42 0 8 3.59 8 8 0 4.42-3.58 8-8 8z"/>
    </svg>
  </div>
  <div class="notification-content">
    <div class="notification-title">Atualização Concluída</div>
    <div class="notification-message">Seu sistema foi atualizado com sucesso para a versão mais recente.</div>
  </div>
  <button aria-label="Fechar notificação" class="close-button" id="closeBtn">&times;</button>
</div>

<script>
  // Função para fechar a notificação
  const closeBtn = document.getElementById('closeBtn');
  const notification = closeBtn.closest('.notification');

  closeBtn.addEventListener('click', () => {
    notification.style.animation = 'slideOutDown 0.4s forwards ease-in';
  });

  notification.addEventListener('animationend', (e) => {
    if (e.animationName === 'slideOutDown') {
      notification.remove();
    }
  });

  // Animação slideOutDown
  const styleSheet = document.createElement('style');
  styleSheet.textContent = `
  @keyframes slideOutDown {
    from {
      transform: translateY(0);
      opacity: 1;
    }
    to {
      transform: translateY(100%);
      opacity: 0;
    }
  }`;
  document.head.appendChild(styleSheet);
</script>
</body>
</html>


