import tkinter.filedialog
import tkinter.ttk as ttk
import tkinter.filedialog
from tkinter import messagebox
import numpy as np
import tkinter as tk
from tkinter.filedialog import *
from PIL import Image, ImageTk
import csv
from PIL import ImageGrab
from copy import deepcopy
import time





root = tk.Tk()
openedImage=None
binaryImage=None
framedImage=None
nCol, nRow, orNRow, orNCol = 0,0,0,0
pixelMapAsString=""
def main():
    global root
    root.geometry("600x450+382+164")
    root.title("New Toplevel")
    root.configure(background="#d9d9d9")
    root.Button1 = tk.Button(root)
    root.Button1.place(relx=0.0, rely=0.0, height=24, width=29)
    root.Button1.configure(activebackground="#ececec")
    root.Button1.configure(activeforeground="#000000")
    root.Button1.configure(background="#d9d9d9")
    root.Button1.configure(disabledforeground="#a3a3a3")
    root.Button1.configure(foreground="#000000")
    root.Button1.configure(highlightbackground="#d9d9d9")
    root.Button1.configure(highlightcolor="black")
    root.Button1.configure(pady="0")
    root.Button1.configure(text='''File''',command=openImage)

    root.Button2 = tk.Button(root)
    root.Button2.place(relx=0.833, rely=0.067, height=24, width=35)
    root.Button2.configure(activebackground="#ececec")
    root.Button2.configure(activeforeground="#000000")
    root.Button2.configure(background="#d9d9d9")
    root.Button2.configure(disabledforeground="#a3a3a3")
    root.Button2.configure(foreground="#000000")
    root.Button2.configure(highlightbackground="#d9d9d9")
    root.Button2.configure(highlightcolor="black")
    root.Button2.configure(pady="0")
    root.Button2.configure(text='''Save''')

    root.Button3 = tk.Button(root)
    root.Button3.place(relx=0.85, rely=0.333, height=24, width=51)
    root.Button3.configure(activebackground="#ececec")
    root.Button3.configure(activeforeground="#000000")
    root.Button3.configure(background="#d9d9d9")
    root.Button3.configure(disabledforeground="#a3a3a3")
    root.Button3.configure(foreground="#000000")
    root.Button3.configure(highlightbackground="#d9d9d9")
    root.Button3.configure(highlightcolor="black")
    root.Button3.configure(pady="0",command=lambda :levialdiAlgorithm(framedImage))
    root.Button3.configure(text='''Levialdi''')

    root.Button4 = tk.Button(root)
    root.Button4.place(relx=0.85, rely=0.6, height=24, width=30)
    root.Button4.configure(activebackground="#ececec")
    root.Button4.configure(activeforeground="#000000")
    root.Button4.configure(background="#d9d9d9")
    root.Button4.configure(disabledforeground="#a3a3a3")
    root.Button4.configure(foreground="#000000")
    root.Button4.configure(highlightbackground="#d9d9d9")
    root.Button4.configure(highlightcolor="black")
    root.Button4.configure(pady="0")
    root.Button4.configure(text='''TSF''')



    root.Label1 = tk.Label(root)
    root.Label1.place(relx=0.833, rely=0.444, height=21, width=72)
    root.Label1.configure(background="#d9d9d9")
    root.Label1.configure(disabledforeground="#a3a3a3")
    root.Label1.configure(foreground="#000000")
    root.Label1.configure(text='''Levialdi nCC''')

    root.Label2 = tk.Label(root)
    root.Label2.place(relx=0.833, rely=0.511, height=21, width=66)
    root.Label2.configure(background="#d9d9d9")
    root.Label2.configure(disabledforeground="#a3a3a3")
    root.Label2.configure(foreground="#000000")
    root.Label2.configure(text='''Levialdi iter''')

    root.Label3 = tk.Label(root)
    root.Label3.place(relx=0.85, rely=0.711, height=21, width=53)
    root.Label3.configure(background="#d9d9d9")
    root.Label3.configure(disabledforeground="#a3a3a3")
    root.Label3.configure(foreground="#000000")
    root.Label3.configure(text='''TSF NCC''')

    root.Text1 = tk.Text(root)
    root.Text1.place(relx=0.0, rely=0.578, relheight=0.431, relwidth=0.357)
    root.Text1.configure(background="white")
    root.Text1.configure(font="TkTextFont")
    root.Text1.configure(foreground="black")
    root.Text1.configure(highlightbackground="#d9d9d9")
    root.Text1.configure(highlightcolor="black")
    root.Text1.configure(insertbackground="black")
    root.Text1.configure(selectbackground="#c4c4c4")
    root.Text1.configure(selectforeground="black")
    root.Text1.configure(width=214)
    root.Text1.configure(wrap='word')

    root.Label4 = tk.Label(root)
    root.Label4.place(relx=0.85, rely=0.8, height=21, width=45)
    root.Label4.configure(background="#d9d9d9")
    root.Label4.configure(disabledforeground="#a3a3a3")
    root.Label4.configure(foreground="#000000")
    root.Label4.configure(text='''TSF iter''')
    root.mainloop()




def openImage():
    try:
        openFileFormats = (("all files", "*.*"), ("png files", "*.png"))  # File formats for easy search
        path = askopenfilename(parent=root, filetypes=openFileFormats)  # Basic file pick gui
        fp = open(path, "rb")  # Read file as a byte map

        global openedImage
        openedImage = Image.open(fp).convert('1', dither=Image.NONE)  # Convert byte map to Image then grayscaling of the image
    except:
        reset()

    imageProcess()
    printImageToSreen(openedImage)
    writeBinaryToScreen()

def printImageToSreen(img):
    render=ImageTk.PhotoImage(img)
    img=Label(root,image=render)
    img.image=render
    img.place(x=10,y=30)
def writeBinaryToScreen():
    global binaryCanvas
    global pixelMapAsString
    fontSize = 3

    # binaryCanvas.create_text(0,0, text=pixelMapAsString, font=("Ariel", fontSize, "bold"), tag="lvTag", anchor=NW)
    # # anchor North West is used to position the image to top left corner
    # # 0,0 gives relative position to anchor

    # for remove text from canvas use tag
    #binaryCanvas.select_clear()
    #binaryCanvas.delete("lvTag")

    #for update you can remove and write text for every iteration
    global Canvas1

    root.Text1 = tk.Text(root)
    root.Text1.place(relx=0.0, rely=0.480, rellheight=0.540, relwidth=0.480)
    root.Text1.configure(width=40, height=6, font=("Arial,4"))
    root.Text1.insert(tk.INSERT, pixelMapAsString)

    binaryCanvas.update()



def imageProcess():
    global openedImage
    nCol, nRow = openedImage.size
    print("-------------------------------------------")
    print("Image size : \nHorizontal : ",nCol,"\nVertical : ", nRow)
    print("-------------------------------------------")

    colorMap = openedImage.load() # Images to pixel map because of converting return average of RGB

    global framedImage
    # Creates an image with 2 additional columns and rows for framing edges
    framedImage = Image.new('RGB', ((nCol+2), (nRow+2)), color='black').convert('1', dither=Image.NONE)
    #convert 1 : black white image
    #convert L : gray scaled image

    for r in range(1,nRow+1):
        for c in range(1,nCol+1):
            framedImage.putpixel((c,r), colorMap[c-1,r-1]) #Coloring framed image

    colorMap = framedImage.load() # Images to pixel map
    orNCol,orNRow=nCol,nRow

    nCol, nRow = framedImage.size
    print("-------------------------------------------")
    print("Framed Image size : \nHorizontal : ", nCol, "\nVertical : ", nRow)
    print("-------------------------------------------")

    global binaryImage
    binaryImage = [[0 for x in range(nCol)] for y in range(nRow)]  # Set pixelValue sizes

    global pixelMapAsString

    #Create binary image according to pixel map
    for r in range(nRow):
        for c in range(nCol):
            if colorMap[c,r] > 200:
                binaryImage[r][c] = 1
            else:
                binaryImage[r][c] = 0
            pixelMapAsString +=  str(binaryImage[r][c])
        pixelMapAsString += "\n"

    print(pixelMapAsString)

    # global Canvas1
    #
    # root.Text1 = tk.Text(root)
    # root.Text1.place(relx=0.0, rely=0.480, rellheight=0.540, relwidth=0.480)
    # root.Text1.configure(width=40, height=6, font=("Arial,4"))
    # root.Text1.insert(tk.INSERT, pixelMapAsString)
    # Putting image to screen


def reset():
    print("")
def levialdiAlgorithm(framedImage):
    ncc=0
    iterLevi=0
    kontrol=True
    copyArray=deepcopy(framedImage)
    copyArray2=deepcopy(framedImage)
    while kontrol:
        kontrol =False
        for i in range (copyArray2.shape[0]):
            for j in range (copyArray2.shape[1]):
                if copyArray2[i][j]==1:
                    if copyArray2[i-1][j-1]==0 and copyArray2[i-1][j]==0 and copyArray2[i-1][j+1]==0 and copyArray2[i][j+1]==0 and copyArray2[i+1][j+1]==0 and copyArray2[i+1][j]==0 and copyArray2[i+1][j-1]==0 and copyArray2[i][j-1]==0:
                        copyArray[i][j]=0
                        kontrol = True
                        ncc=ncc+1
                    if copyArray2[i][j - 1] == 0 and copyArray2[i + 1][j - 1] == 0 and copyArray2[i + 1][j] == 0:
                        copyArray[i][j] = 0
                        kontrol=True
                else :
                    if copyArray2[i][j-1]==1 and copyArray2[i+1][j]==1:
                        copyArray[i][j]=1
                        kontrol =True
    copyArray2=deepcopy(copyArray)
    copyArray2=copyArray2*1
    for q in range(copyArray2.shape[0]):
        for w in range (copyArray2.shape[1]):
            iterLevi+=str(copyArray2[q][1])
        iterLevi+="\n"

        if kontrol:
            iterLevi += 1
    root.Label1.configure(text=ncc)
    return ncc

def bCal (imgarray,i,j):
    b=0
    if imgarray[i-1][j-1]==1: # toplam 1 sayıarına bakıyorum
        b=b+1
    if imgarray[i - 1][j] == 1:
        b=b+1
    if imgarray[i - 1][j + 1] == 1:
        b=b+1
    if imgarray[i][j + 1] == 1:
        b=b+1
    if imgarray[i + 1][j + 1] == 1:
        b=b+1
    if imgarray[i + 1][j] == 1:
        b=b+1
    if imgarray[i + 1][j - 1] == 1:
        b=b+1
    if imgarray[i][j - 1] == 1:
        b=b+1
    return b
def cCal(imgarray,i,j):
    c=0

    if imgarray[i-1][j]==1 and imgarray[i][j+1]==1 and imgarray[i-1][j+1]==0:#  p2 p4 or p4 p6 or p6 p8 or p8 p2 1 olunça köşeleri 0 ise 1 yapıyorum
        imgarray[i-1][j+1]=1
    if imgarray[i][j+1]==1 and imgarray[i+1][j]==1 and imgarray[i+1][j+1]==0:
        imgarray[i+1][j+1]=1
    if imgarray[i][j-1]==1 and imgarray[i+1][j]==1 and imgarray[i+1][j-1]==0:
        imgarray[i+1][j-1]=1
    if imgarray[i-1][j-1]==0 and imgarray[i-1][j]==1 and imgarray[i][j-1]==1:
        imgarray[i-1][j-1]=1
    if imgarray[i-1][j-1]==1: # önçe 0 dan 1 e geçişlere bakıyorum eğer 0 sa bi önçekinin 1 olması durumuna bakıyorum
        if imgarray [i][j-1]==0:
            c=c+1
    if imgarray[i - 1][j] == 1:
        if imgarray[i-1][j-1]==0:
            c = c + 1
    if imgarray[i - 1][j + 1] == 1:
        if imgarray[i-1][j]==0:
            c = c + 1
    if imgarray[i][j + 1] == 1:
        if imgarray[i-1][j+1]==0:
            c = c + 1
    if imgarray[i + 1][j + 1] == 1:
        if imgarray[i][j+1]==0:
            c = c + 1
    if imgarray[i + 1][j] == 1:
        if imgarray[i+1][j+1]==0:
            c = c + 1
    if imgarray[i + 1][j - 1] == 1:
        if imgarray[i+1][j]==0:
            c = c + 1
    if imgarray[i][j - 1] == 1:
        if imgarray[i+1][j-1]==0:
            c = c + 1
    if bCal(imgarray,i,j)==8:
        c=c+1

    return c
def tsfalgorthm(imgarray):

    flag=True
    iteration=0
    kopyArr=deepcopy(imgarray)
    kopyArr2=deepcopy(imgarray)
    ncc=0
    while flag == True:
        iteration=iteration+1
        flag=False
        for i in range(2 , imgarray.shape[0] - 2):  # önçe 0 2 4 6. satırlardaki 1. subfieldları okuyorum
            if i % 2 == 0:
                for j in range(2,imgarray.shape[1] - 2):
                    if j % 2 == 0:
                        if imgarray[i][j] == 1:  # 1 in silme koşulları

                            if bCal(imgarray, i, j) == 0:
                                imgarray[i][j] = 0
                                ncc = ncc + 1
                                flag=True
                            if cCal(imgarray, i, j) ==1:
                                if bCal(imgarray, i, j) == 1:
                                    if imgarray[i - 1][j - 1] ==0 and imgarray[i + 1][j - 1] == 0:
                                        if imgarray[i - 1][j - 1] == 0:
                                            if imgarray[i][j - 1] == 0 and imgarray[i - 1][j] == 0:
                                                imgarray[i][j] = 0
                                                flag=True
                                        if imgarray[i - 1][j] == 0:
                                            if imgarray[i - 1][j - 1] == 0 and imgarray[i - 1][j + 1] == 0:
                                                imgarray[i][j] = 0
                                                flag=True
                                        if imgarray[i - 1][j + 1] == 0:
                                            if imgarray[i - 1][j] == 0 and imgarray[i][j + 1] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i][j + 1] == 0:
                                            if imgarray[i - 1][j + 1] == 0 and imgarray[i + 1][j + 1] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i + 1][j + 1] == 0:
                                            if imgarray[i][j + 1] == 0 and imgarray[i + 1][j] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i + 1][j] == 0:
                                            if imgarray[i + 1][j + 1] == 0 and imgarray[i + 1][j - 1] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i + 1][j - 1] == 0:
                                            if imgarray[i + 1][j] == 0 and imgarray[i][j - 1] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i][j - 1] == 0:
                                            if imgarray[i + 1][j - 1] == 0 and imgarray[i - 1][j - 1] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                else :


                                    if imgarray[i - 1][j - 1] == 0:
                                        if imgarray[i][j - 1] == 0 and imgarray[i - 1][j] == 0:
                                            imgarray[i][j] = 0
                                            flag = True
                                    if imgarray[i - 1][j] == 0:
                                        if imgarray[i - 1][j - 1] == 0 and imgarray[i - 1][j + 1] == 0:
                                            imgarray[i][j] = 0
                                            flag = True
                                    if imgarray[i - 1][j + 1] == 0:
                                        if imgarray[i - 1][j] == 0 and imgarray[i][j + 1] == 0:
                                            imgarray[i][j] = 0
                                            flag = True
                                    if imgarray[i][j + 1] == 0:
                                        if imgarray[i - 1][j + 1] == 0 and imgarray[i + 1][j + 1] == 0:
                                            imgarray[i][j] = 0
                                            flag = True
                                    if imgarray[i + 1][j + 1] == 0:
                                        if imgarray[i][j + 1] == 0 and imgarray[i + 1][j] == 0:
                                            imgarray[i][j] = 0
                                            flag = True
                                    if imgarray[i + 1][j] == 0:
                                        if imgarray[i + 1][j + 1] == 0 and imgarray[i + 1][j - 1] == 0:
                                            imgarray[i][j] = 0
                                            flag = True
                                    if imgarray[i + 1][j - 1] == 0:
                                        if imgarray[i + 1][j] == 0 and imgarray[i][j - 1] == 0:
                                            imgarray[i][j] = 0
                                            flag = True
                                    if imgarray[i][j - 1] == 0:
                                        if imgarray[i + 1][j - 1] == 0 and imgarray[i - 1][j - 1] == 0:
                                            imgarray[i][j] = 0
                                            flag = True
                        if imgarray[i][j] == 0:  # 0'ın silme koşulu
                            if cCal(imgarray, i, j) == 1:
                                if imgarray[i][j - 1] == imgarray[i - 1][j] == 1 or imgarray[i][j - 1] == imgarray[i + 1][j] == 1:
                                    imgarray[i ][j ] = 1
                                    flag=True

        for i in range(2,imgarray.shape[0] - 2):  # 1 3 5 7 satırlardaki 1. subfieldları okuyorum
            if i % 2 == 1:
                for j in range(2,imgarray.shape[1] - 2):
                    if j % 2 == 1:
                        if imgarray[i][j] == 1:  # 1 in silme koşulları
                            if bCal(imgarray, i, j) == 0:
                                imgarray[i][j] = 0
                                ncc = ncc + 1
                                flag = True
                                if cCal(imgarray, i, j) == 1:
                                    if bCal(imgarray, i, j) == 1:
                                        if imgarray[i - 1][j - 1] == 0 and imgarray[i + 1][j - 1] == 0:
                                            if imgarray[i - 1][j - 1] == 0:
                                                if imgarray[i][j - 1] == 0 and imgarray[i - 1][j] == 0:
                                                    imgarray[i][j] = 0
                                                    flag = True
                                            if imgarray[i - 1][j] == 0:
                                                if imgarray[i - 1][j - 1] == 0 and imgarray[i - 1][j + 1] == 0:
                                                    imgarray[i][j] = 0
                                                    flag = True
                                            if imgarray[i - 1][j + 1] == 0:
                                                if imgarray[i - 1][j] == 0 and imgarray[i][j + 1] == 0:
                                                    imgarray[i][j] = 0
                                                    flag = True
                                            if imgarray[i][j + 1] == 0:
                                                if imgarray[i - 1][j + 1] == 0 and imgarray[i + 1][j + 1] == 0:
                                                    imgarray[i][j] = 0
                                                    flag = True
                                            if imgarray[i + 1][j + 1] == 0:
                                                if imgarray[i][j + 1] == 0 and imgarray[i + 1][j] == 0:
                                                    imgarray[i][j] = 0
                                                    flag = True
                                            if imgarray[i + 1][j] == 0:
                                                if imgarray[i + 1][j + 1] == 0 and imgarray[i + 1][j - 1] == 0:
                                                    imgarray[i][j] = 0
                                                    flag = True
                                            if imgarray[i + 1][j - 1] == 0:
                                                if imgarray[i + 1][j] == 0 and imgarray[i][j - 1] == 0:
                                                    imgarray[i][j] = 0
                                                    flag = True
                                            if imgarray[i][j - 1] == 0:
                                                if imgarray[i + 1][j - 1] == 0 and imgarray[i - 1][j - 1] == 0:
                                                    imgarray[i][j] = 0
                                                    flag = True
                                    else:
                                        if imgarray[i - 1][j - 1] == 0:
                                            if imgarray[i][j - 1] == 0 and imgarray[i - 1][j] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i - 1][j] == 0:
                                            if imgarray[i - 1][j - 1] == 0 and imgarray[i - 1][j + 1] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i - 1][j + 1] == 0:
                                            if imgarray[i - 1][j] == 0 and imgarray[i][j + 1] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i][j + 1] == 0:
                                            if imgarray[i - 1][j + 1] == 0 and imgarray[i + 1][j + 1] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i + 1][j + 1] == 0:
                                            if imgarray[i][j + 1] == 0 and imgarray[i + 1][j] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i + 1][j] == 0:
                                            if imgarray[i + 1][j + 1] == 0 and imgarray[i + 1][j - 1] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i + 1][j - 1] == 0:
                                            if imgarray[i + 1][j] == 0 and imgarray[i][j - 1] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i][j - 1] == 0:
                                            if imgarray[i + 1][j - 1] == 0 and imgarray[i - 1][j - 1] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                            if imgarray[i][j] == 0:  # 0'ın silme koşulu
                                if cCal(imgarray, i, j) == 1:
                                    if imgarray[i][j - 1] == imgarray[i - 1][j] == 1 or imgarray[i][j - 1] ==imgarray[i + 1][j] == 1:
                                        imgarray[i][j] = 1
                                        flag=True
        for i in range(2,imgarray.shape[0] - 2):  # 0 2 4 6 satırlardaki 2. subfieldları okuyorum
            if i % 2 == 0:
                for j in range(2,imgarray.shape[1] - 2):
                    if j % 2 == 1:
                        if imgarray[i][j] == 1:  # 1 in silme koşulları
                            if bCal(imgarray, i, j) == 0:
                                imgarray[i][j] = 0
                                ncc = ncc + 1
                                flag = True
                                if cCal(imgarray, i, j) == 1:
                                    if bCal(imgarray, i, j) == 1:
                                        if imgarray[i - 1][j - 1] == 0 and imgarray[i + 1][j - 1] == 0:
                                            if imgarray[i - 1][j - 1] == 0:
                                                if imgarray[i][j - 1] == 0 and imgarray[i - 1][j] == 0:
                                                    imgarray[i][j] = 0
                                                    flag = True
                                            if imgarray[i - 1][j] == 0:
                                                if imgarray[i - 1][j - 1] == 0 and imgarray[i - 1][j + 1] == 0:
                                                    imgarray[i][j] = 0
                                                    flag = True
                                            if imgarray[i - 1][j + 1] == 0:
                                                if imgarray[i - 1][j] == 0 and imgarray[i][j + 1] == 0:
                                                    imgarray[i][j] = 0
                                                    flag = True
                                            if imgarray[i][j + 1] == 0:
                                                if imgarray[i - 1][j + 1] == 0 and imgarray[i + 1][j + 1] == 0:
                                                    imgarray[i][j] = 0
                                                    flag = True
                                            if imgarray[i + 1][j + 1] == 0:
                                                if imgarray[i][j + 1] == 0 and imgarray[i + 1][j] == 0:
                                                    imgarray[i][j] = 0
                                                    flag = True
                                            if imgarray[i + 1][j] == 0:
                                                if imgarray[i + 1][j + 1] == 0 and imgarray[i + 1][j - 1] == 0:
                                                    imgarray[i][j] = 0
                                                    flag = True
                                            if imgarray[i + 1][j - 1] == 0:
                                                if imgarray[i + 1][j] == 0 and imgarray[i][j - 1] == 0:
                                                    imgarray[i][j] = 0
                                                    flag = True
                                            if imgarray[i][j - 1] == 0:
                                                if imgarray[i + 1][j - 1] == 0 and imgarray[i - 1][j - 1] == 0:
                                                    imgarray[i][j] = 0
                                                    flag = True
                                    else:
                                        if imgarray[i - 1][j - 1] == 0:
                                            if imgarray[i][j - 1] == 0 and imgarray[i - 1][j] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i - 1][j] == 0:
                                            if imgarray[i - 1][j - 1] == 0 and imgarray[i - 1][j + 1] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i - 1][j + 1] == 0:
                                            if imgarray[i - 1][j] == 0 and imgarray[i][j + 1] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i][j + 1] == 0:
                                            if imgarray[i - 1][j + 1] == 0 and imgarray[i + 1][j + 1] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i + 1][j + 1] == 0:
                                            if imgarray[i][j + 1] == 0 and imgarray[i + 1][j] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i + 1][j] == 0:
                                            if imgarray[i + 1][j + 1] == 0 and imgarray[i + 1][j - 1] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i + 1][j - 1] == 0:
                                            if imgarray[i + 1][j] == 0 and imgarray[i][j - 1] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i][j - 1] == 0:
                                            if imgarray[i + 1][j - 1] == 0 and imgarray[i - 1][j - 1] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                            if imgarray[i][j] == 0:  # 0'ın silme koşulu
                                if cCal(imgarray, i, j) == 1:
                                    if imgarray[i][j - 1] == imgarray[i - 1][j] == 1 or imgarray[i][j - 1] == imgarray[i + 1][j] == 1:
                                        imgarray[i][j] = 1
                                        flag=True
        for i in range(2,imgarray.shape[0] - 2):  # 1 3 5 7 satırlardaki subfieldları okuyorum
            if i % 2 == 1:
                for j in range(2,imgarray.shape[0] - 2):
                    if i % 2 == 0:
                        if imgarray[i][j] == 1:  # 1 in silme koşulları
                            if bCal(imgarray, i, j) == 0:
                                imgarray[i][j] = 0
                                ncc = ncc + 1
                                flag = True
                                if cCal(imgarray, i, j) == 1:
                                    if bCal(imgarray, i, j) == 1:
                                        if imgarray[i - 1][j - 1] == 0 and imgarray[i + 1][j - 1] == 0:
                                            if imgarray[i - 1][j - 1] == 0:
                                                if imgarray[i][j - 1] == 0 and imgarray[i - 1][j] == 0:
                                                    imgarray[i][j] = 0
                                                    flag = True
                                            if imgarray[i - 1][j] == 0:
                                                if imgarray[i - 1][j - 1] == 0 and imgarray[i - 1][j + 1] == 0:
                                                    imgarray[i][j] = 0
                                                    flag = True
                                            if imgarray[i - 1][j + 1] == 0:
                                                if imgarray[i - 1][j] == 0 and imgarray[i][j + 1] == 0:
                                                    imgarray[i][j] = 0
                                                    flag = True
                                            if imgarray[i][j + 1] == 0:
                                                if imgarray[i - 1][j + 1] == 0 and imgarray[i + 1][j + 1] == 0:
                                                    imgarray[i][j] = 0
                                                    flag = True
                                            if imgarray[i + 1][j + 1] == 0:
                                                if imgarray[i][j + 1] == 0 and imgarray[i + 1][j] == 0:
                                                    imgarray[i][j] = 0
                                                    flag = True
                                            if imgarray[i + 1][j] == 0:
                                                if imgarray[i + 1][j + 1] == 0 and imgarray[i + 1][j - 1] == 0:
                                                    imgarray[i][j] = 0
                                                    flag = True
                                            if imgarray[i + 1][j - 1] == 0:
                                                if imgarray[i + 1][j] == 0 and imgarray[i][j - 1] == 0:
                                                    imgarray[i][j] = 0
                                                    flag = True
                                            if imgarray[i][j - 1] == 0:
                                                if imgarray[i + 1][j - 1] == 0 and imgarray[i - 1][j - 1] == 0:
                                                    imgarray[i][j] = 0
                                                    flag = True
                                    else:
                                        if imgarray[i - 1][j - 1] == 0:
                                            if imgarray[i][j - 1] == 0 and imgarray[i - 1][j] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i - 1][j] == 0:
                                            if imgarray[i - 1][j - 1] == 0 and imgarray[i - 1][j + 1] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i - 1][j + 1] == 0:
                                            if imgarray[i - 1][j] == 0 and imgarray[i][j + 1] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i][j + 1] == 0:
                                            if imgarray[i - 1][j + 1] == 0 and imgarray[i + 1][j + 1] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i + 1][j + 1] == 0:
                                            if imgarray[i][j + 1] == 0 and imgarray[i + 1][j] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i + 1][j] == 0:
                                            if imgarray[i + 1][j + 1] == 0 and imgarray[i + 1][j - 1] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i + 1][j - 1] == 0:
                                            if imgarray[i + 1][j] == 0 and imgarray[i][j - 1] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                                        if imgarray[i][j - 1] == 0:
                                            if imgarray[i + 1][j - 1] == 0 and imgarray[i - 1][j - 1] == 0:
                                                imgarray[i][j] = 0
                                                flag = True
                            if imgarray[i][j] == 0:  # 0'ın silme koşulu
                                if cCal(imgarray, i, j) == 1:
                                    if imgarray[i][j - 1] == imgarray[i - 1][j] == 1 or imgarray[i][j - 1] == imgarray[i + 1][j] == 1:
                                        imgarray[i][j] = 1
                                        flag=True
    print(iteration)
    return ncc

if __name__ == '__main__':
    main()
