import { Component } from '@angular/core';

@Component({
  selector: 'app-home',
  templateUrl: './home.component.html',
  styleUrls: ['./home.component.css']
})
export class HomeComponent {
  title = "Welcome to Cute Doll Store 🧸💖";
}
<div class="hero">
  <h1>{{title}}</h1>
  <p>Beautiful Dolls for Everyone</p>
  <button routerLink="/dolls">Shop Now</button>
</div>
.hero{
  text-align:center;
  padding:60px;
  background:linear-gradient(to right,#ff9ecf,#ffc0cb);
  color:white;
}
button{
  padding:10px 20px;
  background:white;
  color:#ff1493;
  border:none;
  border-radius:20px;
  font-weight:bold;
}
import { Component } from '@angular/core';

@Component({
  selector: 'app-dolls',
  templateUrl: './dolls.component.html',
  styleUrls: ['./dolls.component.css']
})
export class DollsComponent {

  dolls = [
    { name: "Barbie Doll", price: 999, image: "assets/dolls/barbie.jpg", rating: 4 },
    { name: "Teddy Bear Doll", price: 599, image: "assets/dolls/teddy.jpg", rating: 5 },
    { name: "Baby Doll", price: 799, image: "assets/dolls/baby.jpg", rating: 3 }
  ];

  cart:any[] = [];

  addToCart(doll:any){
    this.cart.push(doll);
    alert("Added to Cart!");
  }
}
<div class="container">
  <div class="card" *ngFor="let doll of dolls">
    <img [src]="doll.image">
    <h3>{{doll.name}}</h3>
    <p>₹{{doll.price}}</p>

    ⭐ Rating:
    <span *ngFor="let star of [1,2,3,4,5]">
      <span [style.color]="star <= doll.rating ? 'gold' : 'gray'">★</span>
    </span>

    <button (click)="addToCart(doll)">Add to Cart</button>
  </div>
</div>
.container{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
  gap:20px;
  padding:20px;
}
.card{
  background:#fff0f5;
  padding:15px;
  border-radius:15px;
  text-align:center;
}
.card img{
  width:100%;
  height:200px;
  object-fit:cover;
}
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';

import { HomeComponent } from './home/home.component';
import { DollsComponent } from './dolls/dolls.component';
import { CartComponent } from './cart/cart.component';
import { LoginComponent } from './login/login.component';
import { RegisterComponent } from './register/register.component';

const routes: Routes = [
 { path:'', component:HomeComponent },
 { path:'dolls', component:DollsComponent },
 { path:'cart', component:CartComponent },
 { path:'login', component:LoginComponent },
 { path:'register', component:RegisterComponent }
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }
import { AppRoutingModule } from './app-routing.module';

imports: [
  BrowserModule,
  AppRoutingModule
],
<router-outlet></router-outlet>
