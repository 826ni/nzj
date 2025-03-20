<!DOCTYPE html>
<html lang="zh-CN">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>按钮交互示例</title>
  <style>
    body {
      background-color: pink;
      margin: 0;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      font-family: '华文彩云', cursive;
    }

    img {
      width: 20vw;
      height: auto;
      margin: 10px 0;  /* 减少图片的上下边距 */
    }

    .text-box {
      width: 600px;
      height: 200px;
      padding: 20px;
      margin: 10px 0;  /* 减少文本框的上下边距 */
      border: none;
      outline: none;
      background-color: transparent;
      color: blue;
      text-align: center;
      font-family: '华文彩云', cursive;
      font-size: 48px;
    }

    .button-container {
      display: flex;
      gap: 40px;  /* 减少按钮之间的间距 */
      margin-top: 10px;  /* 减少按钮容器的上边距 */
    }

    button {
      padding: 30px 60px;
      font-size: 2.4em;
      transition: all 0.3s;
      cursor: pointer;
    }

    button:hover {
      transform: scale(1.1);
    }

    button:disabled {
      opacity: 0.5;
      cursor: not-allowed;
    }
  </style>
</head>

<body>
  <img src="omen.JPG" alt="本地图片">
  <textarea class="text-box" placeholder="你喜欢omen宝宝吗"></textarea>
  <div class="button-container">
    <button id="leftButton">喜欢</button>
    <button id="rightButton">不喜欢</button>
  </div>

  <script>
    const leftButton = document.getElementById('leftButton');
    const rightButton = document.getElementById('rightButton');
    const textBox = document.querySelector('.text-box');

    let leftClickCount = 0;
    const leftMaxClicks = 1;
    let rightClickCount = 0;
    const rightMaxClicks = 4;

    const leftButtonTexts = ["宝宝最好啦！"];
    const rightButtonTexts = [
      "真的不可以喜欢omen吗",
      "求求你啦",
      "omen会乖乖的",
      "宝宝最好啦！"
    ];

    function handleButtonClick(event) {
      const button = event.target;

      if (button.id === 'leftButton') {
        if (leftClickCount >= leftMaxClicks) return;
        leftClickCount++;
        textBox.value = leftButtonTexts[leftClickCount - 1];
      }

      if (button.id === 'rightButton') {
        if (rightClickCount >= rightMaxClicks) return;
        rightClickCount++;
        textBox.value = rightButtonTexts[rightClickCount - 1];
      }

      const currentWidth = parseInt(window.getComputedStyle(button).width, 10);
      const currentHeight = parseInt(window.getComputedStyle(button).height, 10);
      button.style.width = currentWidth + 40 + 'px';
      button.style.height = currentHeight + 20 + 'px';

      if (button.id === 'leftButton' && leftClickCount >= leftMaxClicks) {
        button.disabled = true;
      }
      if (button.id === 'rightButton' && rightClickCount >= rightMaxClicks) {
        button.disabled = true;
      }
    }

    leftButton.addEventListener('click', handleButtonClick);
    rightButton.addEventListener('click', handleButtonClick);
  </script>
</body>
</html>
