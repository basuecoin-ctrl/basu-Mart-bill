<!DOCTYPE html>
<html>
<head>
<title>Shop Billing</title>
</head>

<body>

<h2>Shop Billing System</h2>

Product:
<input list="products" id="product">

<datalist id="products">
<option value="Rice">
<option value="Dal">
<option value="Sugar">
<option value="Oil">
<option value="Salt">
<option value="Milk">
<option value="Tea">
<option value="Biscuits">
<option value="Soap">
<option value="Shampoo">
</datalist>

<br><br>

Price: <input type="number" id="price"><br><br>

Quantity (Kg/Piece): <input type="number" id="qty"><br><br>

<button onclick="addItem()">Add Item</button>

<h3>Bill Items</h3>

<table border="1" id="billTable">
<tr>
<th>Product</th>
<th>Price</th>
<th>Qty</th>
<th>Total</th>
</tr>
</table>

<h2 id="grandTotal">Total: 0</h2>

<button onclick="printBill()">Print Bill</button>

<script>

let total = 0;

function addItem(){

let product = document.getElementById("product").value;
let price = document.getElementById("price").value;
let qty = document.getElementById("qty").value;

let itemTotal = price * qty;

total += itemTotal;

let table = document.getElementById("billTable");

let row = table.insertRow();

row.insertCell(0).innerHTML = product;
row.insertCell(1).innerHTML = price;
row.insertCell(2).innerHTML = qty;
row.insertCell(3).innerHTML = itemTotal;

document.getElementById("grandTotal").innerHTML = "Total: " + total;

}

function printBill(){
window.print();
}

</script>

</body>
</html>
