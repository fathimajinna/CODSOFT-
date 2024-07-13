from tkinter import*
root=Tk()
root.geometry('800x800')
datas=[]
def add():
    global datas
    datas.append([Name.get(),Number.get(),email.get(),address.get(1.0,"end-1c")])
    update_book()
def view():
    
        selected_index = int(select.curselection()[0])
        Name.set(datas[selected_index][0])
        Number.set(datas[selected_index][1])
        email.set(datas[selected_index][2])
        address.delete(1.0, "end-1c")
        address.insert(1.0, datas[selected_index][3])
    
 
def delete():
    del datas[int(select.curselection()[0])]
    update_book()

def update_book():
    select.delete(0,END)
    for n,(name,number,email,address) in enumerate(datas):
        select.insert(END,f"{idx+1}.{data[0]}")

def search():
     query=search.get().lower()
     select.delete(0,END)
     for idx,data in enumerate(datas):
         if query in data[0].lower() or query in data[1].lower() or query in data[2].lower() or query in data[3].lower():
             select.insert(END, f"{idx+1}.{data[0]}")





Name=StringVar()
Number=StringVar()
email=StringVar()
search=StringVar()

frame=Frame()
frame.pack(pady=10)

frame1=Frame()
frame1.pack()

frame2=Frame()
frame2.pack(pady=10)


frame3=Frame()
frame3.pack(pady=10)

frame4=Frame()
frame4.pack(pady=10)


Label(frame,text='Name',font='ivy 13 bold').pack(side=LEFT)
Entry(frame,textvariable=Name,width=50).pack()

Label(frame1,text='Number',font='ivy 13 bold').pack(side=LEFT)
Entry(frame1,textvariable=Number,width=50).pack()


Label(frame2,text='email',font='ivy 13 bold').pack(side=LEFT)
Entry(frame2,textvariable=email,width=50).pack()


Label(frame3,text='address',font='ivy 13 bold').pack(side=LEFT)
address=Text(frame3,width=45,height=10)
address.pack()

Label(frame4,text='search',font='ivy 13 bold').pack(side=LEFT)
Entry(frame4,textvariable=email,width=50).pack()

Button(root,text="ADD",font="ivy 13 bold",command=add).place(x=100,y=350)
Button(root,text="DELETE",font="ivy 13 bold",command=delete).place(x=200,y=350)
Button(root,text="VIEW",font="ivy 13 bold",command=view).place(x=300,y=350)
Button(root,text="SEARCH",font="ivy 13 bold",command=search).place(x=400,y=350)

frame5=FRAME()
frame5.pack(pady=20)

select=Listbox(frame5,height=20)
select.pack()

root.mainloop()