class RMS:
    #RMS (Restaurant Management System)
    def __init__(self,restaurant_name,restaurant_menu):
        self.user_bill=0
        self.user_order=''
        self.user_pay=0
        self.menu=restaurant_menu
        self.rest_name=restaurant_name
        
    def welcome_user(self):
        #Welcome User
        print('Welcome to',self.rest_name)
    
    def display_menu(self):
        
        #Display Menu
        for i in self.menu:
            print(i.title(),self.menu[i])
    
    
    def take_order(self):#Take Order
        
        self.user_order=input('Please place your order here:')
    
    
    def prepare_order(self):#Prepare Order
        
        import time 
        print('Preparing your',self.user_order.title())
        time.sleep(0.5)
        self.user_bill=self.user_bill+self.menu[self.user_order]
    def serve_order(self):#Serve Order
        print('Your order is ready!')
        print('Please enjoy your',self.user_order.title())
    
    def display_bill(self):#Display Bill
        print('Your Total Bill:',self.user_bill)
        
    def verify_payment(self):#Verify Payment
        
        self.user_pay=int(input('Please pay your bill here:'))
        
        while self.user_pay<self.user_bill:
            print('Invalid Payment!')
            self.user_bill=self.user_bill-self.user_pay
            print('Please pay remaining',self.user_bill)
            self.user_pay=int(input('Please pay your bill here:'))
            
        if self.user_pay>self.user_bill:
            print('Payment Successful!')
            print('Here is your change:',self.user_pay-self.user_bill)
        else:
            pass
    def thank_user(self):#Thank User
        print('Thank you for visiting',self.rest_name)
        
    def order_process(self):
        self.display_menu()
        self.take_order()
        
        if self.user_order.lower() in self.menu:
            self.prepare_order()
            self.serve_order()
            self.user_rep=input('Do you want to order again?')
            while self.user_rep.lower()=='yes':
                self.repeat_order()
                self.user_rep=input('Do you want to order again?')
                    
            self.display_bill()
            self.verify_payment()
            self.thank_user()
        else:
            print('Invalid Order!')
            self.order_process()
            
    def repeat_order(self):
        self.display_menu()
        self.take_order()
        if self.user_order.lower() in self.menu:
            self.prepare_order()
            self.serve_order()
        else:
            print('Invalid Order')
            self.repeat_order()

rn='Moonlight Cafe'
rm={'frappe':200,'cold coffee':200,'drip coffee':190}
moonlight_cafe=RMS(rn,rm)

moonlight_cafe.welcome_user()
moonlight_cafe.order_process()

          

#import Liabrary
import tkinter as tk
#create Window
window=tk.Tk()
#Change title of window
window.title('RMS')
# change window size
window.geometry('400x400')
#window buttons and Lable
tk.Label(window,text='Welcome to',font=('Times now',9)).place (x=160,y=20)
tk.Label(window,text='Moonlight Cafe',font=('Times now',19)).place(x=110,y=60)
tk.Button(window,text='Menu Card',width=20,command=moonlight_cafe.order_process).place(x=120,y=150)
# mainloon command 
window.mainloop()
