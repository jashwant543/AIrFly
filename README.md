# AIrFly
# AI-Powered Flight Booking Assistant

A GenAI-powered conversational flight booking assistant built with **Spring Boot**, **Spring AI**, and **OpenAI**.  
The application supports natural language chat, tool calling, Retrieval-Augmented Generation, vector search, PDF-based knowledge ingestion, and persistent chat memory.

## Features

- Conversational AI assistant using Spring AI `ChatClient`
- OpenAI integration for LLM-based responses
- Tool calling / function calling using Spring AI `@Tool`
- Flight booking operations through natural language
  - Create flight booking
  - View user bookings
  - Update booking status
- Retrieval-Augmented Generation using PDF documents
- PDF ingestion with token-based text splitting
- Vector embeddings and semantic search
- PgVector-based vector store
- JDBC-backed chat memory for user-specific conversations
- Custom token usage advisor for tracking token consumption and response latency
- REST API-based backend architecture

## Tech Stack

- Java 21
- Spring Boot
- Spring AI
- OpenAI
- RAG
- Tool Calling
- PgVector
- PostgreSQL
- Spring Data JPA
- JDBC Chat Memory
- Vector Embeddings
- Semantic Search
- Maven
- Lombok

## Key GenAI Concepts Used
  Large Language Models
  OpenAI Integration
  Prompt Engineering
  Tool Calling
  Function Calling
  Retrieval-Augmented Generation
  Vector Embeddings
  Semantic Search
  PgVector Vector Database
  Chat Memory
  AI Advisors
  Token Usage Tracking
  Context-Aware Responses
  Future Enhancements
  Add authentication and authorization
  Store token usage metrics in database
  Add streaming AI responses
  Add frontend chat UI
  Add support for multiple document uploads
  Add observability and tracing for AI calls
  Improve prompt safety using guardrails

## Demo

<video width="700" controls>
  <source src="https://raw.githubusercontent.com/jashwant543/AIrFly/main/assets/Demo.mp4" type="video/mp4">
</video>

## System Architecture

```mermaid
flowchart TD
    U["User / Client"] --> API["Spring Boot REST API"]

    API --> CC["Spring AI ChatClient"]
    CC --> LLM["OpenAI LLM"]

    CC --> MEM["Chat Memory Advisor"]
    MEM --> JDBC["JDBC Chat Memory Repository"]

    CC --> TOOLS["Tool Calling Layer"]
    TOOLS --> FBT["FlightBookingTools"]
    FBT --> FBS["FlightBookingService"]
    FBS --> REPO["FlightBookingRepository"]
    REPO --> DB["PostgreSQL Database"]

    CC --> RAG["RAG Advisors"]
    RAG --> VS["PgVector Vector Store"]

    PDF["FAQ PDF"] --> READER["PDF Document Reader"]
    READER --> SPLITTER["Token Text Splitter"]
    SPLITTER --> EMB["Embedding Model"]
    EMB --> VS

    CC --> TOKEN["TokenUsageAdvisor"]

