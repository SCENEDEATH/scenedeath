<div class="card">
          <h3>Блог: Первые шаги</h3>
          <p>Описание опубликованного блога.</p>
        </div>
      </section>
    </div>
  </div>

  <script>
    // Функция проверки доступа по пин-коду
    function checkAccess() {
      // Предупреждение об эпилепсии
      alert("Внимание: на сайте присутствуют мерцающие элементы, которые могут вызвать приступ эпилепсии. Если вы чувствительны к мерцающему свету, будьте осторожны!");
      // Запрос пин-кода
      var pin = prompt("Для входа в сайт введите пин-код:");
      if (pin !== "5246") {
        alert("Неверный пин-код!");
        window.location.href = "https://google.com"; // Перенаправление при неправильном пин-коде
      } else {
        document.getElementById("mainContent").style.display = "block";
      }
    }

    // Функция для резкого мерцающего фона
    function changeBackground() {
      // Случайная задержка от 6 до 10 секунд
      let delay = Math.floor(Math.random() * (10000 - 6000 + 1)) + 6000;
      setTimeout(() => {
        // Резко меняем фон на черно-белый
        document.body.style.background = "linear-gradient(to bottom right, black, white)";
        // Через 50 мс возвращаем исходный черно-красный фон и запускаем цикл заново
        setTimeout(() => {
          document.body.style.background = "linear-gradient(to bottom right, black, red)";
          changeBackground();
        }, 50);
      }, delay);
    }

    // Функция для настройки навигации между секциями
    function setupNavigation() {
      const navLinks = document.querySelectorAll('nav a');
      const sections = document.querySelectorAll('.section');

      navLinks.forEach(link => {
        link.addEventListener('click', function(e) {
          e.preventDefault();
          // Скрываем все секции
          sections.forEach(section => section.classList.remove('active'));
          // Показываем выбранную секцию
          const sectionId = this.getAttribute('data-section');
          document.getElementById(sectionId).classList.add('active');
        });
      });
    }

    // Функция для случайного переключения на шрифт Nightcore (используется шрифт Rye)
    function toggleNightcoreFont() {
      let delay = Math.floor(Math.random() * (15000 - 10000 + 1)) + 10000; // задержка от 10 до 15 секунд
      setTimeout(() => {
        document.body.classList.add("nightcore");
        // Оставляем эффект на 3 секунды, затем возвращаем исходный стиль
        setTimeout(() => {
          document.body.classList.remove("nightcore");
          toggleNightcoreFont(); // Рекурсивный вызов для повторения эффекта
        }, 3000);
      }, delay);
    }

    // При загрузке страницы сначала проверяем доступ, затем запускаем фон, навигацию и эффект Nightcore
    window.onload = function() {
      checkAccess();
      changeBackground();
      setupNavigation();
      toggleNightcoreFont();
    };
  </script>
</body>
</html>
