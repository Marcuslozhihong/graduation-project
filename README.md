# graduation-project
class Product():
    def __init__(self):
        self.products = {
            "001": {
                "name": "Oreo",
                "price": "2.50",
                "stock": 89
            },
            "002":{
                "name": "Chips Ahoy",
                "price": "2.75",
                "stock": 45
            },
            "003": {
                "name": "Coca-Cola",
                "price": "1.50",
                    "stock": 120
            },
            "004":{
                "name": "Pepsi",
                "price": "1.50",
                "stock": 100
            }
        }
    
    def display_product(self):
        print("Available Products: 001 - Oreo, 002 - Chips Ahoy, 003 - Coca-Cola, 004 - Pepsi")

class ShoppingCart():
    def __init__(self):
        self.cartlist = []


    def display_all(self):
        print(self.cartlist)


    def check_stock(self):
        check_item = input("Enter the item you want to check: ")
        if check_item in self.cartlist:
            print(check_item, "is in stock")
        else:
            print(check_item, "is not in stock")


    def add_item(self):
        
        add_item = input("Enter the number of the item you want to add: ")
        if add_item not in self.cartlist:
            if add_item in product.products.keys():
                num_items = int(input("Enter the quantity of items you want to add: "))
                tempList = [add_item, num_items]
                if num_items > product.products[add_item]["stock"]:
                    print("Not enough stock available")
                    return False
                else:
                    print("Item is available")
                    print("Item added to cart")
                    self.cartlist.append(tempList)
                    product.products[add_item]["stock"] -= num_items
            else:
                print("Item not found")
        else:
            print("Item already in cart")
        print(cart.cartlist)
    

    def remove_item(self):
        item_removed = input("Enter the number of item you want to remove: ")
        self.cartlist.remove(item_removed)
        print(cart.cartlist)
        

    def checkout(self):
        total_price = 0

        print("Checking out with the following items:")
        for sublist in self.cartlist:
            item_num = sublist[0]
            item_quantity = sublist[1]
            item_price = float(product.products[item_num]['price'])
            item_name = product.products[item_num]['name']
            total_price += item_price * item_quantity
            print(f"{item_name} - {item_quantity} @ ${item_price:.2f} each")
        
        print("Thank you for your purchase!")
        print("Total price: $", total_price)


product = Product()
cart = ShoppingCart()




print("Welcome to The Food Cartel's online store!")
print("Please select an option:")
print("1. View Products")
print("2. Add Item to Cart")
print("3. Remove Item from Cart")
print("4. Check Stock")
print("5. Check your cart")
print("6. Checkout")
option = input("Enter your choice: ")
while option != "6":
    if option == "1":
        product.display_product()
    elif option == "2":
        cart.add_item()
    elif option == "3":
        cart.remove_item()
    elif option == "4":
        cart.check_stock()
    elif option == "5":
        cart.checkout()
    else:
        print("This option does not exist please try again")
    print("1. View Products")
    print("2. Add Item to Cart")
    print("3. Remove Item from Cart")
    print("4. Check Stock")
    print("5. Check your cart")
    print("6. Checkout")
    option = input("Enter your choice: ")

cart.checkout()
print("Thank you for shopping with us!")
cart.cartlist.clear()
