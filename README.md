# Named Entity Recognition from PDF using UiPath RPA and AI Center

This UiPath project automates the extraction of named entities from PDF documents using an AI-based NER (Named Entity Recognition) model. It integrates with UiPath AI Center or ML Services to identify key fields such as names, emails, skills, education, and more, and structures the output into an Excel sheet.

## Overview

The workflow reads a PDF file as input and processes it using the Named Entity Recognition (NER) activity. The NER activity returns a JSON string containing detected entities with their corresponding types. The robot then deserializes this JSON, groups the text entries by type, and writes the structured data into an Excel file where each entity type is a column.

## Workflow Summary

1. Read text from PDF file
2. Pass the text to the NER model (via AI Center or ML Skill activity)
3. Receive JSON output with detected entities
4. Deserialize the JSON
5. Group entities by their type (e.g., Name, Email, Skills, etc.)
6. Build a DataTable with columns for each type
7. Write the DataTable into an Excel file

## Input Format

The input is a standard PDF document such as a resume, report, or form.

## Output Format

The output is an Excel file with one row of structured information extracted from the PDF. For example:

| Name    | Phone    | Email    | Skills         | Education         | Experience      | Certification     |
| ------- | -------- | -------- | -------------- | ----------------- | --------------- | ----------------- |
| \[Name] | \[Phone] | \[Email] | Python, SQL... | B.Tech, School... | Internship, Job | AI Basics, IOT... |

## Technologies Used

* UiPath Studio
* UiPath AI Center / ML Services (NER activity)
* UiPath.Web.Activities (for JSON parsing)
* Excel Activities
* VB.NET collections (Dictionary, DataTable)

## Prerequisites

* UiPath Studio (latest version)
* PDF file containing unstructured text
* Connected NER ML Skill (via AI Center or endpoint)
* UiPath Excel and Web dependencies installed

## How to Use

1. Open the project in UiPath Studio
2. Place the PDF file in the designated folder (or update the path)
3. Run the workflow
4. The output Excel file will be saved to the specified location

## Notes

* The workflow assumes the NER JSON structure is an array of objects, each containing `text` and `type` fields.
* Multiple entities of the same type are combined into comma-separated values under each column.
