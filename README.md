<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<title>Floating Message Wall</title>
<style>
  body {
    margin: 0;
    font-family: sans-serif;
    background: linear-gradient(#ffb347, #ffcc33);
    overflow: hidden;
  }

  /* ฉาก */
  #scene {
    position: relative;
    width: 100vw;
    height: 100vh;
  }

  /* กล่องข้อความลอย */
  .floating {
    position: absolute;
    padding: 12px 20px;
    background: rgba(255,255,255,0.9);
    border-radius: 30px;
    white-space: nowrap;
    animation: float 20s linear infinite;
    box-shadow: 0 4px 10px rgba(0,0,0,0.2);
    font-size: 18px;
  }

  @keyframes float {
    from {
      transform: translateX(110vw);
    }
    to {
      transform: translateX(-120%);
    }
  }

  /* กล่อง input */
  #control {
    position: fixed;
    bottom: 20px;
    left: 50%;
    transform: translateX(-50%);
    background: white;
    padding: 15px;
    border-radius: 15px;
    box-shadow: 0 5px 15px rgba(0,0,0,0.3);
  }

  input {
    padding: 8px;
    font-size: 16px;
    width: 220px;
  }

  button {
    padding: 8px 14px;
    font-size: 16px;
    margin-left: 5px;
    cursor: pointer;
  }
</style>
</head>
<body>

<div id="scene"></div>

<div id="control">
  <input type="text" id="textInput" placeholder="พิมพ์ข้อความของคุณ">
  <button onclick="addMessage()">ส่งข้อความ</button>
</div>

<script>
function addMessage() {
  const text = document.getElementById("textInput").value;
  if (!text) return;

  const msg = document.createElement("div");
  msg.className = "floating";
  msg.textContent = text;

  // สุ่มตำแหน่งแนวตั้ง
  msg.style.top = Math.random() * 80 + "vh";

  // สุ่มความเร็ว
  msg.style.animationDuration = (15 + Math.random() * 15) + "s";

  document.getElementById("scene").appendChild(msg);
  document.getElementById("textInput").value = "";
}
</script>

</body>
</html>
