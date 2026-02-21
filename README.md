# Meeting-Scheduler-Agent

Intelligent RAG-Based Meeting Scheduler (Fully Local)

An intelligent, low-latency meeting scheduling system built using a Retrieval-Augmented Generation (RAG) architecture.
This system compresses calendar data, learns user preferences using vector embeddings, and optimizes meeting time suggestions — all without using any external API keys.


### Table of Contents:

1. Project Overview  
2. Problem Statement  
3. System Features  
4. System Architecture  
5. RAG Pipeline  
6. Calendar Compression Strategy  
7. Scheduling Optimization  
8. Technology Stack  
9. Project Structure  
10. Installation Guide  
11. API Documentation  
12. Example Workflow  
13. Future Enhancements   


1. Project Overview

The Intelligent Meeting Scheduler is a fully local RAG-based system that:
i) Compresses calendar data
ii) Stores preferences using vector embeddings
iii) Retrieves contextual memory via FAISS
iv) Generates optimized meeting suggestions
v) Minimizes scheduling latency
Unlike traditional schedulers, this system uses vector similarity search to personalize scheduling decisions.


2. Problem Statement

Traditional scheduling systems:
i) Store verbose calendar logs
ii) Lack contextual understanding of user preferences
iii) Have high latency for large datasets
iv) Do not optimize intelligently
This project solves:
i) Redundant calendar storage
ii) Inefficient meeting slot selection
iii) Lack of personalization
iv) Scalability limitations


3. System Features

i) Fully local (No API keys required)  
ii) Fast vector search using FAISS  
iii) Semantic preference understanding  
iv) Calendar compression for reduced memory  
v) Optimized slot ranking algorithm  
vi) Modular backend architecture  
vii) Easily extensible  


4. System Architecture

a) Core Components:
  >> API Layer:
     Handles incoming calendar, preference, and scheduling requests.
  >> Compression Layer:
     Merges overlapping busy time slots to reduce storage.
  >> Embedding Layer:
     Uses SentenceTransformers to generate 384-dimensional embeddings.
  >> Vector Store:
     FAISS in-memory index for fast similarity search.
  >> Retriever:
     Finds relevant user preference context.
  >> Scheduler Engine:
     Detects available time slots within working hours.
  >> Optimizer
     Ranks slots based on preference scoring.


5. RAG Pipeline

This system implements Retrieval-Augmented Generation without external LLM APIs.
Step 1: Query Creation:
User requests meeting duration.
Step 2: Embedding Generation:
Query converted into 384-dimension vector.
Step 3: Vector Retrieval:
FAISS retrieves relevant preference data.
Step 4: Context Assembly:
Retrieved metadata compiled into context.
Step 5: Slot Generation:
Free intervals computed from compressed calendar.
tep 6: Optimization:
Slots ranked based on preference matching.


6. Calendar Compression Strategy

>> Calendars often contain:
i) Overlapping time blocks
ii) Redundant intervals
iii) Repeated busy periods
>> Compression Techniques
i) Interval merging  
ii) Sorted time normalization  
iii) Reduced metadata storage  
>> Benefits:
i) Reduced memory
ii) Faster scheduling
iii) Smaller vector index


7. Scheduling Optimization

Slot Generation Algorithm:
i) Sort busy intervals  
ii) Identify gaps  
iii) Validate duration  
iv) Return valid slots  
Ranking Formula:
Score = PreferenceWeight
  >> ConflictPenalty
  >> FragmentationPenalty
Preference boosts include:
i) Morning preference
ii) Afternoon preference
iii) Custom keyword matching


8. Technology Stack

Layer => Technology
i) Backend => FastAPI
ii) Embeddings => SentenceTransformers 
iii) Vector DB => FAISS 
iv) Optimization => Custom Python Algorithm 
v) Deployment => Uvicorn / Docker 
vi) Language => Python 3.9+ 


9. Project Structure

=> Document:
a) Architecture.md
b) RAG-Pipeline.md
c) Compression-Strategy.md
d) Vector-Search.md
e) Scheduler-Optimization.md
f) API-Ddesign.md
g) Deployment.md

=> Backend
a) main.py
b) models.py
c) embeddings.py
d) vector_store.py
e) compressor.py
f) scheduler.py
g) retriever.py
h) optimizer.py
i) rag_engine.py

=> Data
a) sample_calendar.json

=> README.md


10. Installation Guide

Step 1: Clone Repository
Step 2: Install Dependencies
Step 3: Run Server
Interactive Swagger UI will appear.


11. API Usage

Add Calendar
POST `/add_calendar`


1️2. Example Workflow

a) User uploads calendar
b) System compresses busy slots
c) User adds preference
d) Preference stored as embedding
e) User requests meeting
f) Context retrieved from FAISS
g)Free slots computed
h) Ranked suggestions returned


13. Future Enhancements

a) Multi-user conflict resolution
b) Distributed vector database
c) Reinforcement learning preference tuning
d) Graph-based meeting optimization
e) Persistent FAISS storage
f) React frontend dashboard
g) Docker & Kubernetes deployment
