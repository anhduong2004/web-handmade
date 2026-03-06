<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<title>Cửa hàng Handmade</title>

<style>

body{
font-family: Arial;
margin:0;
background:#f6f6f6;
}

header{
background:#ff7a7a;
color:white;
padding:15px;
display:flex;
justify-content:space-between;
align-items:center;
}

nav a{
color:white;
margin:10px;
text-decoration:none;
font-weight:bold;
}

.container{
width:90%;
margin:auto;
margin-top:20px;
}

.products{
display:grid;
grid-template-columns:repeat(3,1fr);
gap:20px;
}

.product{
background:white;
padding:15px;
border-radius:10px;
box-shadow:0 0 5px rgba(0,0,0,0.2);
text-align:center;
}

.product img{
width:100%;
height:200px;
object-fit:cover;
}

button{
background:#ff7a7a;
color:white;
border:none;
padding:10px;
cursor:pointer;
border-radius:5px;
}

.cart{
position:fixed;
right:20px;
bottom:20px;
background:white;
padding:15px;
border-radius:10px;
box-shadow:0 0 10px rgba(0,0,0,0.3);
width:250px;
}

</style>
</head>

<body>

<header>

<h2>Handmade Shop</h2>

<nav>
<a href="#">Trang chủ</a>
<a href="#">Sản phẩm</a>
<a href="#">Giỏ hàng</a>
</nav>

</header>


<div class="container">

<h2>Sản phẩm handmade</h2>

<input type="text" id="search" placeholder="Tìm sản phẩm..." onkeyup="searchProduct()">

<div class="products" id="productList">

<div class="product">
<img src="https://picsum.photos/300/200">
<h3>Vòng tay handmade</h3>
<p>150.000đ</p>
<button onclick="addCart('Vòng tay handmade',150000)">Thêm vào giỏ</button>
</div>

<div class="product">
<img src="https://picsum.photos/301/200">
<h3>Túi vải handmade</h3>
<p>250.000đ</p>
<button onclick="addCart('Túi vải handmade',250000)">Thêm vào giỏ</button>
</div>

<div class="product">
<img src="https://picsum.photos/302/200">
<h3>Móc khóa handmade</h3>
<p>50.000đ</p>
<button onclick="addCart('Móc khóa handmade',50000)">Thêm vào giỏ</button>
</div>

</div>

</div>


<div class="cart">

<h3>Giỏ hàng</h3>

<ul id="cartList"></ul>

<p>Tổng: <span id="total">0</span>đ</p>

<button onclick="checkout()">Thanh toán</button>

</div>


<script>

let cart=[]
let total=0

function addCart(name,price){

cart.push({name,price})

total+=price

updateCart()

}

function updateCart(){

let list=document.getElementById("cartList")
list.innerHTML=""

cart.forEach(item=>{

let li=document.createElement("li")

li.innerText=item.name+" - "+item.price+"đ"

list.appendChild(li)

})

document.getElementById("total").innerText=total

}

function checkout(){

alert("Đặt hàng thành công!")

cart=[]
total=0
updateCart()

}

function searchProduct(){

let input=document.getElementById("search").value.toLowerCase()

let products=document.querySelectorAll(".product")

products.forEach(p=>{

let name=p.innerText.toLowerCase()

if(name.includes(input))
p.style.display="block"
else
p.style.display="none"

})

}

</script>

</body>
</html>
