"""
Script designed to parse an excel sheet to retrieve residues from a column of choice, starting
at a given row. The output is a list that can be used in Pymol scripts
"""

import openpyxl
import string
import os

#auxiliar functions

def residify(col,row,sheet):
    "Creates a list of residues in col starting at row in sheet to be used in Pymol."
    residues = []
    i = int(row)

    while True:
        to_parse = sheet["F"+str(i)].value
        parsing = ""
        if to_parse == None:
            break

        for ch in to_parse:
            if ch in string.digits:
                parsing += ch
        residues.append("resi "+parsing)

        i += 1

    return residues


# main body
while True:
    raw_path = input("Input the desired path (or leave blank to exit): ")
    # exit the loop
    if raw_path == "":
        break
    raw_sheet = input("Input the desired sheet (blank defaults to whichever is active): ")
    col = input("Enter the desired column: ")
    row = input("Enter the desired starting row: ")

    path = os.path.normpath(raw_path)

    # parsing
    wb = openpyxl.load_workbook(path)

    if raw_sheet == "": # blank default
        sheet = wb.active
    else:
        sheet = wb.get_sheet_by_name(raw_sheet)

    print(residify(col,row,sheet))
