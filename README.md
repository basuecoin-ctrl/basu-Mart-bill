<script>

let total = 0;

function addItem(){

let product = document.getElementById("product").value;
let price = parseFloat(document.getElementById("price").value);
let qty = parseFloat(document.getElementById("qty").value);
let unit = document.getElementById("unit").value;

if(product=="" || isNaN(price) || isNaN(qty)){
alert("Fill all fields");
return;
}

let itemTotal = price * qty;
total += itemTotal;

let table = document.getElementById("billTable");

let row = table.insertRow(-1);

let c1 = row.insertCell(0);
let c2 = row.insertCell(1);
let c3 = row.insertCell(2);
let c4 = row.insertCell(3);
let c5 = row.insertCell(4);
let c6 = row.insertCell(5);

c1.innerHTML = product;
c2.innerHTML = price;
c3.innerHTML = qty;
c4.innerHTML = unit;
c5.innerHTML = itemTotal;

let delBtn = document.createElement("button");
delBtn.innerHTML = "Delete";

delBtn.onclick = function(){

total -= itemTotal;
document.getElementById("grandTotal").innerHTML = "Total: " + total;
table.deleteRow(row.rowIndex);

};

c6.appendChild(delBtn);

document.getElementById("grandTotal").innerHTML = "Total: " + total;

}

function printBill(){
window.print();
}

</script>
