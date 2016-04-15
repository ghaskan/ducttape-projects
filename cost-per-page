"""
Reads .pdf files to extract their page number and calculate printing price
for 1 slide per page, 2 slides per page, and 4 slides per page.
"""

import os
import PyPDF2
import math

def count_pages(path):
    "Opens a given .pdf file and returns its number of pages."

    pdfFileObj = open(path, "rb")
    pdfReader = PyPDF2.PdfFileReader(pdfFileObj)

    return pdfReader.numPages

def euros_cents(n):
    "Converts an input of euros.cents (eg: 3.7) into euros and cents (eg: 3e70cents)."

    euros = int(n)
    cents = round((n - euros) * 100)
    output = str(euros)+" euros and "+str(cents)+" cents."

    return output

def two_slides(n):
    "Calculates the total price for printing n pages with two slides per page."

    price = 0.03
    total = price * math.ceil(n / 2)

    return euros_cents(total)

def four_slides(n):
    "Calculates the total price for printing n pages with four slides per page."

    price = 0.03
    total = price * math.ceil(n / 4)

    return euros_cents(total)


while True:
    # path can point to a directory or file.
    raw_path = input("Input the desired path (or leave blank to exit): ")
    # exit the loop
    if raw_path == "":
        break

    # if the path point to a file
    if os.path.isfile(raw_path):
        path = os.path.normpath(raw_path)
        n = count_pages(path)
        print(two_slides(n))
        print(four_slides(n))

    # if the path points to a directory
    elif os.path.isdir(raw_path):
        n = 0
        file_list = os.listdir(raw_path)
        
        for file in file_list:
            if file.endswith('.pdf'):
                file_path = os.path.join(raw_path, file)
                n += count_pages(file_path)

        # results!
        print("price: ",euros_cents(0.03*n))
        print("two slides per page: ",two_slides(n))
        print("four slides per page: ",four_slides(n))
