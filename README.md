<!DOCTYPE html>
<html>
<head>
<title>Shop Billing System</title>

<style>
body{
font-family: Arial;
padding:20px;
}

input,select,button{
padding:8px;
margin:5px;
}

table{
border-collapse: collapse;
width:100%;
margin-top:20px;
}

th,td{
border:1px solid black;
padding:8px;
text-align:center;
}

button{
cursor:pointer;
}
</style>

</head>

<body>

<h2>Shop Billing System</h2>

Product:
<input list="products" id="product" placeholder="Type product name">

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

Price:
<input type="number" id="price" placeholder="Price">

Qty:
<input type="number" id="qty" placeholder="Quantity">

Unit:
<select id="unit">
<option value="Kg">Kg</option>
<option value="Piece">Piece</option>
</select>

<button onclick="addItem()">Add Item</button>

<h3>Bill Items</h3>

<table id="billTable">
<tr>
<th>Product</th>
<th>Price</th>
<th>Qty</th>
<th>Unit</th>
<th>Total</th>
<th>Delete</th>
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
let unit = document.getElementById("unit").value;

if(product=="" || price=="" || qty==""){
alert("Please fill all fields");
return;
}

let itemTotal = price * qty;

total += itemTotal;

let table = document.getElementById("billTable");

let row = table.insertRow();

row.insertCell(0).innerHTML = product;
row.insertCell(1).innerHTML = price;
row.insertCell(2).innerHTML = qty;
row.insertCell(3).innerHTML = unit;
row.insertCell(4).innerHTML = itemTotal;

let delBtn = document.createElement("button");
delBtn.innerHTML = "X";

delBtn.onclick = function(){

total -= itemTotal;

document.getElementById("grandTotal").innerHTML = "Total: " + total;

table.deleteRow(row.rowIndex);

}

row.insertCell(5).appendChild(delBtn);

document.getElementById("grandTotal").innerHTML = "Total: " + total;

document.getElementById("product").value="";
document.getElementById("price").value="";
document.getElementById("qty").value="";

}

function printBill(){
window.print();
}

</script>

</body>
</html>
