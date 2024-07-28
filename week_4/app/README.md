# Project Setup Instructions

Follow these steps to set up and run the project on your local machine.

## Step 1: Set Environment Variables

Set the `POSTGRES_HOST` environment variable to point to your local database:

```bash
export POSTGRES_HOST=localhost
```

## Step 2: Build and Start Docker Containers

Navigate to the project directory and build the Docker containers:

```bash
cd week_4/app
docker-compose build
```

Start the Docker containers in detached mode:

```bash
docker-compose up -d
```

![docker](/week_4/app/static/020_docker.png)

## Step 3: Prepare the Database

Run the preparation script to initialize and index the database:

```bash
python prep.py
```

**Expected Output:**
```
Initializing database...
Indexing process completed successfully!
```

## Step 4: Manage Docker Containers

### Stop the Streamlit Container

Stop the Streamlit container if it is currently running:

```bash
docker-compose stop streamlit
```

**Expected Output:**
```bash
WARN[0001] /path/to/docker-compose.yaml: `version` is obsolete 
[+] Stopping 1/1
 ✔ Container streamlit  Stopped 
```

### Rebuild the Streamlit Container

Rebuild the Streamlit container to apply any updates:

```bash
docker-compose build streamlit
```

### Start the Streamlit Container

Start the Streamlit container:

```bash
docker-compose start streamlit
```

**Expected Output:**
```bash
WARN[0000] /path/to/docker-compose.yaml: `version` is obsolete 
[+] Running 1/1
 ✔ Container streamlit  Started  
```

## Step 5: Create Elasticsearch Index

Create an Elasticsearch index for course questions:

```bash
curl -X PUT "localhost:9200/course-questions"
```

**Expected Output:**
```json
{"acknowledged":true,"shards_acknowledged":true,"index":"course-questions"}
```

## Step 6: Generate Data

Run the data generation script:

```bash
python generate_data.py
```

**Expected Output:**
```bash
Script started at 2024-07-28 11:44:35.897850+02:00
Generating historical data from 2024-07-28 05:44:35.897890+02:00 to 2024-07-28 11:44:35.897890+02:00
Starting historical data generation from 2024-07-28 05:44:35.897890+02:00 to 2024-07-28 11:44:35.897890+02:00
Saved conversation: ID=345dea0d-a07e-4f75-b6dc-cc12c75a7a03, Time=2024-07-28 05:44:35.897890+02:00, Course=machine-learning-zoomcamp, Model=ollama/llama3
Saved feedback for conversation 345dea0d-a07e-4f75-b6dc-cc12c75a7a03: Negative
Saved conversation: ID=2611169f-d0be-47da-8cb3-407a09aa51ba, Time=2024-07-28 05:50:35.897890+02:00, Course=data-engineering-zoomcamp, Model=ollama/mistral
Saved feedback for conversation 2611169f-d0be-47da-8cb3-407a09aa51ba: Positive
Saved conversation: ID=2cb7f94d-796d-4caf-b001-6205a7954cd6, Time=2024-07-28 06:05:35.897890+02:00, Course=data-engineering-zoomcamp, Model=ollama/phi3
Saved feedback for conversation 2cb7f94d-796d-4caf-b001-6205a7954cd6: Positive
Saved conversation: ID=3ea3948e-c00a-4fe3-a9e7-34244e5f5c3b, Time=2024-07-28 06:09:35.897890+02:00, Course=data-engineering-zoomcamp, Model=ollama/llama3
Saved feedback for conversation 3ea3948e-c00a-4fe3-a9e7-34244e5f5c3b: Positive
Saved conversation: ID=bb35449b-6786-4804-923e-3970c88e045a, Time=2024-07-28 06:24:35.897890+02:00, Course=machine-learning-zoomcamp, Model=ollama/llama3
Saved feedback for conversation bb35449b-6786-4804-923e-3970c88e045a: Positive
Saved conversation: ID=aff2e0ba-2c73-4461-805a-07e6b79456f9, Time=2024-07-28 06:27:35.897890+02:00, Course=machine-learning-zoomcamp, Model=ollama/mistral
Saved feedback for conversation aff2e0ba-2c73-4461-805a-07e6b79456f9: Positive
Saved conversation: ID=4cd5fdb7-6043-4aff-9508-0a98392f1778, Time=2024-07-28 06:31:35.897890+02:00, Course=mlops-zoomcamp, Model=ollama/phi3
Saved feedback for conversation 4cd5fdb7-6043-4aff-9508-0a98392f1778: Negative
Saved conversation: ID=c7061077-8cfb-4150-9726-f793c3b4071f, Time=2024-07-28 06:35:35.897890+02:00, Course=mlops-zoomcamp, Model=ollama/mistral
Saved feedback for conversation c7061077-8cfb-4150-9726-f793c3b4071f: Positive
Saved conversation: ID=15f83a7d-f755-4c1d-aea8-3a4e18542504, Time=2024-07-28 06:46:35.897890+02:00, Course=machine-learning-zoomcamp, Model=ollama/llama3
Saved feedback for conversation 15f83a7d-f755-4c1d-aea8-3a4e18542504: Positive
Saved conversation: ID=8cf755d0-f512-40d7-9e5c-f36e24cdd6c7, Time=2024-07-28 06:56:35.897890+02:00, Course=mlops-zoomcamp, Model=ollama/llama3
Saved feedback for conversation 8cf755d0-f512-40d7-9e5c-f36e24cdd6c7: Positive
Generated 10 conversations so far...
Saved conversation: ID=979f9298-0032-4dec-b53e-969298e4a785, Time=2024-07-28 07:03:35.897890+02:00, Course=mlops-zoomcamp, Model=ollama/mistral
Saved feedback for conversation 979f9298-0032-4dec-b53e-969298e4a785: Positive
Saved conversation: ID=e2fae3b8-01a1-4cf1-ae19-6454322f62c8, Time=2024-07-28 07:05:35.897890+02:00, Course=machine-learning-zoomcamp, Model=ollama/mistral
Saved conversation: ID=a598abd3-0bc8-481b-8e89-fe1583f5d2bb, Time=2024-07-28 07:14:35.897890+02:00, Course=machine-learning-zoomcamp, Model=ollama/llama3
Saved conversation: ID=a695bd59-878b-4d22-b4bd-0d316a032dc3, Time=2024-07-28 07:21:35.897890+02:00, Course=mlops-zoomcamp, Model=ollama/mistral
Saved conversation: ID=f585e935-da6c-4c85-8f90-93fc3a1e4720, Time=2024-07-28 07:28:35.897890+02:00, Course=machine-learning-zoomcamp, Model=ollama/mistral
Saved feedback for conversation f585e935-da6c-4c85-8f90-93fc3a1e4720: Positive
Saved conversation: ID=7c63057e-a352-40b1-922e-fb56e2a1b238, Time=2024-07-28 07:41:35.897890+02:00, Course=mlops-zoomcamp, Model=ollama/mistral
Saved conversation: ID=a4b8cc1c-e211-4d71-8cc9-b2484a47a812,

 Time=2024-07-28 07:52:35.897890+02:00, Course=data-engineering-zoomcamp, Model=ollama/llama3
Saved feedback for conversation a4b8cc1c-e211-4d71-8cc9-b2484a47a812: Positive
Saved conversation: ID=ed61b863-dea1-472d-88c9-49337f9686e1, Time=2024-07-28 07:53:35.897890+02:00, Course=data-engineering-zoomcamp, Model=ollama/llama3
Saved conversation: ID=1c74645f-e569-4294-817e-4f8f14790cfa, Time=2024-07-28 07:54:35.897890+02:00, Course=data-engineering-zoomcamp, Model=ollama/llama3
Saved conversation: ID=683057d0-e8d6-4b71-8509-cf9906df9f4a, Time=2024-07-28 07:56:35.897890+02:00, Course=machine-learning-zoomcamp, Model=ollama/phi3
Saved feedback for conversation 683057d0-e8d6-4b71-8509-cf9906df9f4a: Positive
```

**Q: I just discovered the course. Can I still join it?**

>You should see this


![streamlit](/week_4/app/static/010_streamlit.png)

## Grafana Dashboard

![grafana](/week_4/app/static/030_grafana.png)

This concludes the setup instructions. Happy learning!