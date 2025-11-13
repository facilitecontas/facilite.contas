<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Pix Swap Local</title>
  <style>body{font-family:Arial; padding:20px;}</style>
</head>
<body>
  <h2>Pix Swap (Offline)</h2>
  <textarea id="qr" placeholder="Cole o payload Pix aqui..." style="width:100%;height:100px;"></textarea><br><br>
  <input type="number" id="valor" placeholder="Novo valor (ex: 15.50)" step="0.01"><br><br>
  <button onclick="swap()">Trocar Valor</button>
  <pre id="out"></pre>

  <script>
  function crc16(s) {
    let crc = 0xFFFF;
    for (let i = 0; i < s.length; i++) {
      crc ^= s.charCodeAt(i) << 8;
      for (let j = 0; j < 8; j++) crc = crc & 0x8000 ? (crc << 1) ^ 0x1021 : crc << 1;
    }
    return (crc & 0xFFFF).toString(16).toUpperCase().padStart(4,'0');
  }
  function swap() {
    let qr = document.getElementById('qr').value.trim();
    let valor = parseFloat(document.getElementById('valor').value).toFixed(2);
    qr = qr.replace(/6304....$/i, '');
    qr = qr.replace(/54\d{2}[\d.]+/, `54${(valor.length+'').padStart(2,'0')}${valor}`);
    const crc = crc16(qr + '6304');
    document.getElementById('out').textContent = qr + '6304' + crc;
  }
  </script>
</body>
</html>
