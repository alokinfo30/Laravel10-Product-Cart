**To run Project **

git clone https://github.com/alokinfo30/Laravel10-Product-Cart.git
cd Laravel10-Product-Cart
php artisan migrate
composer update
php artisan serve


Development Steps:

Step 1: Download Laravel Project

composer create-project laravel/laravel --prefer-dist Project-name

Step 2: Add Database Details .env file.

Step 3: Create Model and Migrations

php artisan make:model Book and add fillable columns
php artisan make:migration create_books_table
php artisan migrate

protected $fillable = [
        'name', 
        'author', 
        'image', 
        'price'
    ];    

    $table->string("name", 255)->nullable();
            $table->text("author")->nullable();
            $table->string("image", 255)->nullable();
            $table->decimal("price", 6, 2);    

Step 4: Populate Records in Database (Dummy data)

php artisan make:seed BookSeeder
php artisan db:seed --class=BookSeeder

Step 5: Build Product Controller

php artisan make:controller BookController

Step 6: Create New Routes

Route::get('/shopping-cart', [BookController::class, 'bookCart'])->name('shopping.cart');

in view route(route-name) or  route(route-name, id)
Step 7: Create Cart View

<div class="container mt-4">
    @if(session('success'))
        <div class="alert alert-success">
          {{ session('success') }}
        </div> 
    @endif
    @yield('content')
</div>



@extends('shop')
   
@section('content')
    @yield('content')
</div>
@foreach($books as $book)
    {{ $book->name }}
    {{ $book->author }}
    @endforeach
</div>
    
@endsection

Step 8: Add Products to Cart using session

        @if(session('cart'))
            @foreach(session('cart') as $id => $details)

            ${{ $details['price'] }}
            {{ $details['name'] }}
         @endforeach
        @endif


        **Concept**

        $book = Book::findorFail($id);
        $cart =session()->get('cart', []);
        
        
Step 8: Add Products to Cart
