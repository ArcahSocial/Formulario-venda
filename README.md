<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Venda de Mudas</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background-color: #f5f5f5;
      margin: 0;
      padding: 20px;
    }
    h1 {
      text-align: center;
      color: #2f6d3b;
    }
    form {
      max-width: 800px;
      margin: auto;
      background-color: #ffffff;
      padding: 30px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    label {
      display: block;
      margin-bottom: 6px;
      font-weight: bold;
      color: #333;
    }
    input, select, textarea {
      width: 100%;
      padding: 10px;
      margin-bottom: 20px;
      border: 1px solid #ccc;
      border-radius: 6px;
      box-sizing: border-box;
    }
    input[readonly] {
      background-color: #eee;
    }
    button {
      background-color: #4CAF50;
      color: white;
      padding: 12px 20px;
      border: none;
      border-radius: 6px;
      cursor: pointer;
      font-size: 16px;
    }
    button:hover {
      background-color: #45a049;
    }
  </style>
</head>
<body>

  <h1>Registro de Venda de Mudas</h1>

  <form>

    <label for="data">Data da Venda</label>
    <input type="date" id="data" name="data" required>

    <label for="especie">Espécie da Muda</label>
    <select id="especie" name="especie" required>
      <option value="">Selecione a Espécie</option>
      <option>Alface Americana</option>
      <option>Alface Crespa</option>
      <option>Alface Roxa</option>
      <option>Alface Mimosa</option>
      <option>Acelga Chinesa</option>
      <option>Rúcula</option>
      <option>Salsa</option>
      <option>Couve</option>
      <option>Coentro</option>
      <option>Cebolinha</option>
    </select>

    <label for="forma_venda">Forma de Venda</label>
    <select id="forma_venda" name="forma_venda" required>
      <option value="">Selecione</option>
      <option value="unidade">Por Unidade</option>
      <option value="kg">Por Kg</option>
    </select>

    <label for="quantidade">Quantidade Vendida</label>
    <input type="number" id="quantidade" name="quantidade" min="0.1" step="0.1" required>

    <label for="valor_unitario">Valor Unitário (R$)</label>
    <input type="number" id="valor_unitario" name="valor_unitario" step="0.01" min="0" required>

    <label for="valor_total">Valor Total da Venda (R$)</label>
    <input type="number" id="valor_total" name="valor_total" readonly>

    <label for="comprador">Nome do Comprador</label>
    <input type="text" id="comprador" name="comprador" required>

    <label for="pagamento">Forma de Pagamento</label>
    <select id="pagamento" name="pagamento" required>
      <option value="">Selecione</option>
      <option>Dinheiro</option>
      <option>PIX</option>
      <option>Cartão de Crédito</option>
      <option>Cartão de Débito</option>
      <option>Outro</option>
    </select>

    <label for="responsavel">Responsável pela Venda</label>
    <input type="text" id="responsavel" name="" required>

    <label for="obs">Observações</label>
    <textarea id="obs" name="obs" rows="4" placeholder="Alguma observação importante..."></textarea>

    <button type="submit">Salvar Venda</button>
  </form>

  <script>
    // Preencher data com o dia atual
    const dataHoje = new Date().toISOString().split('T')[0];
    document.getElementById('data').value = dataHoje;

    // Preencher responsável padrão
    document.getElementById('responsavel').value = "";

    // Calcular valor total automaticamente
    const quantidade = document.getElementById("quantidade");
    const valorUnitario = document.getElementById("valor_unitario");
    const valorTotal = document.getElementById("valor_total");
    const formaVenda = document.getElementById("forma_venda");

    function calcularTotal() {
      const qtd = parseFloat(quantidade.value);
      const unit = parseFloat(valorUnitario.value);
      if (!isNaN(qtd) && !isNaN(unit)) {
        valorTotal.value = (qtd * unit).toFixed(2);
      } else {
        valorTotal.value = "";
      }
    }

    quantidade.addEventListener("input", calcularTotal);
    valorUnitario.addEventListener("input", calcularTotal);
    formaVenda.addEventListener("change", calcularTotal);
  </script>

</body>
</html>
