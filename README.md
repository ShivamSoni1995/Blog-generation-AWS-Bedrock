# Generative AI Blog Generation Application on AWS

## Project Overview

This project demonstrates how to build an end-to-end serverless generative AI application on AWS to automatically generate blog content. Users can send a query via an API, which triggers a Lambda function. This function then leverages foundation models from Amazon Bedrock to generate the blog post and stores the result in an S3 bucket.

This README provides a guide to understanding the architecture, services used, and the steps involved in developing and testing this application.

## Table of Contents

1.  [Architecture](#architecture)
2.  [AWS Services Used](#aws-services-used)
3.  [Core Components & Logic](#core-components--logic)
    * [API Gateway](#api-gateway)
    * [AWS Lambda](#aws-lambda)
    * [Amazon Bedrock](#amazon-bedrock)
    * [Amazon S3](#amazon-s3)
4.  [Prerequisites](#prerequisites)
5.  [Step-by-Step Implementation Guide](#step-by-step-implementation-guide)
    * [1. Setting up Amazon Bedrock Access](#1-setting-up-amazon-bedrock-access)
    * [2. Creating the S3 Bucket](#2-creating-the-s3-bucket)
    * [3. Developing the AWS Lambda Function](#3-developing-the-aws-lambda-function)
    * [4. Creating the API with API Gateway](#4-creating-the-api-with-api-gateway)
6.  [Lambda Function Details](#lambda-function-details)
    * [Runtime](#runtime)
    * [Core Logic](#core-logic)
    * [Error Handling](#error-handling)
    * [Permissions](#permissions)
7.  [Testing the Application](#testing-the-application)
8.  [Logging and Debugging](#logging-and-debugging)
9.  [Future Enhancements](#future-enhancements)

## Architecture

The application follows this high-level architecture:

1.  **User/Client (e.g., Postman)**: Sends a POST request with a query/topic for the blog post.
2.  **Amazon API Gateway**: Receives the request, acts as the front door for the application, and triggers the AWS Lambda function.
3.  **AWS Lambda**:
    * Receives the query from API Gateway.
    * Interacts with Amazon Bedrock, sending the query to a chosen foundational model.
    * Receives the generated blog content from Bedrock.
    * Saves the generated blog content as a file (text/PDF) in an Amazon S3 bucket, timestamped for uniqueness.
4.  **Amazon Bedrock**: Provides access to various foundational models (e.g., Llama 3, Anthropic Claude) that generate the blog content based on the prompt.
5.  **Amazon S3**: Stores the generated blog files.
