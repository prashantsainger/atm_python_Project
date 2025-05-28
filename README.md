# atm_python_Project

from tkinter import *
import time

root = Tk()
root.geometry("900x850")
root.title("ATM MACHINE")
root.config(bg = "black")

Tops = Frame(root, bg = "white",width=800 , height=50, relief=SUNKEN)
Tops.pack(side="top")

f1 = Frame(root, bg = "black", width=300 , height=700, relief=SUNKEN)
f1.pack(side="left")

f2 = Frame(root, bg = "black", width=400 , height=700, relief=SUNKEN)
f2.pack(side="right")

localtime = time.asctime(time.localtime(time.time()))

lbl1 = Label(Tops ,font=("arial" ,25,"bold") ,text="ATM MACHINE", fg="white" , bg="black" , bd=10 , anchor='w')
lbl1.grid(row=0,column=0)

lbl2 = Label(Tops ,font=("arial" ,15,"bold") ,text=localtime, fg="white" , bg="black" , bd=10 , anchor='w')
lbl2.grid(row=1,column=0)

number = StringVar()
amount = StringVar()
withd = StringVar()
acca = "  "

def bank():
    global acca
    accno = ["356211","247896","456896"]
    account =  number.get()
    if account in accno :
        label.config(text="Registered User")
        bank = {"356211":20000,"247896":30000,"456896":40000}
        balance = bank[account]
        acca = balance
    else:
        label.config(text="No Registered User")
        

def deposit():
    global acca
    amo = float(amount.get())
    bal = acca + amo
    label3.config(text=("Net Balance :",str(bal)))
        


def withdrawn() :
    global acca
    wd = float(withd.get())
    if acca>=wd :
        acc = acca-wd
        label4.config(text=("Net Balance :",str(acc))) 
    else:
        label4.config(text="Insufficient Balance") 


def bal():
    global acca
    label5.config(text=("Net Balance :", str(acca))) 
        


def reset():
    number.get()
    amount.get()
    withd.get()
    label.config(text="")
    label3.config(text="") 
    label4.config(text="") 
    label5.config(text="") 
    
        
lbl = Label(f1,font=("arial" ,20,"bold"),fg="white" ,bg="black" , bd=10 ,text="Enter account number :",anchor='w')
lbl.grid(row=0,column=3)
text = Entry(f1,font=("arial" ,20,"bold"),fg="white" , bg="blue" , bd=10 ,textvariable=number,justify="right",insertwidth=4)
text.grid(row=0,column=4)
label = Label(f1,font=("arial" ,20,"bold"),fg="white" , bg="black" , bd=10 )
label.grid(row=1,column=4)
btnsubmit = Button(f2, padx = 14 ,pady = 4 ,bd=10, fg="black",font=("arial" ,20,"bold"),width=7,text="SUBMIT",bg="white",command=bank )
btnsubmit.grid(row=0,column=4)

lblTotal = Label(f1,text="  ",fg="white",bg="black")
lblTotal.grid(row=3,columnspan=10)


        
lbl = Label(f1,font=("arial" ,20,"bold"),fg="white" , bg="black" , bd=10 ,text="Enter amount to be deposited :",anchor='w')
lbl.grid(row=2,column=3)
text = Entry(f1,font=("arial" ,20,"bold"),fg="white" , bg="blue" , bd=10 ,textvariable=amount,justify="right",insertwidth=4)
text.grid(row=2,column=4)
label3 = Label(f1,font=("arial" ,20,"bold"),fg="white" , bg="black" )
label3.grid(row=3,column=4)
btndeposit = Button(f2, padx = 14 ,pady = 4 ,bd=10, fg="black",font=("arial" ,20,"bold"),width=7,text="DEPOSIT",bg="white",command=deposit)
btndeposit.grid(row=1,column=4)

lblTotal = Label(f1,text="  ",fg="white",bg="black")
lblTotal.grid(row=7,columnspan=10)


lbl = Label(f1,font=("arial" ,20,"bold"),fg="white" , bg="black" , bd=10 ,text="Enter amount to be withdrawn :",anchor='w')
lbl.grid(row=4,column=3)
text = Entry(f1,font=("arial" ,20,"bold"),fg="white" , bg="blue" , bd=10 ,textvariable=withd,justify="right",insertwidth=4) 
text.grid(row=4,column=4)
label4 = Label(f1,font=("arial" ,20,"bold"),fg="white" , bg="black" )
label4.grid(row=5,column=4)

label5 = Label(f1,font=("arial" ,20,"bold"),fg="white" , bg="black" )
label5.grid(row=10,column=4)

btnwithdraw = Button(f2, padx = 14 ,pady = 4 ,bd=10, fg="black",font=("arial" ,20,"bold"),width=7,text="WITHDRAWN",bg="white",command=withdrawn)
btnwithdraw.grid(row=2,column=4)

btnbal = Button(f2, padx = 14 ,pady = 4 ,bd=10, fg="black",font=("arial" ,20,"bold"),width=7,text="BALANCE",bg="white",command=bal)
btnbal.grid(row=10,column=4)
btnreset = Button(f2, padx = 14 ,pady = 4 ,bd=10, fg="black",font=("arial" ,20,"bold"),width=7,text="RESET",bg="white",command=reset)
btnreset.grid(row=11,column=4)

btnexit = Button(f2, padx = 14 ,pady = 4 ,bd=10, fg="black",font=("arial" ,20,"bold"),width=7,text="EXIT",bg="white",command=root.destroy)
btnexit.grid(row=12,column=4)



root.mainloop()
