# Natural Language Queries in Egocentric Videos

## Table of Contents
- [Project Overview](#project-overview)
- [Methodology](#methodology)
    - [Dataset](#dataset)
- [Notebooks](#notebooks)
- [Environment Setup](#environment-setup)
- [References](#references)

## Project Overview
<div align="center" style="padding: 40px 0;">
  <img src="images/ego4d_overview.png" alt="ego4d_overview" width="600">
  <div style="font-size: 14px; color: gray; margin-top: 10px;">
    <em>Figure 1: Frames of egocentric videos taken from the Ego4D dataset <a href="#references">[1]</a>.</em>
    <br>
  </div>
</div>

Egocentric Vision captures human interactions from a privileged viewpoint, thanks to cameras mounted directly on the head of the user performing the actions. The release of large-scale datasets, such as EPIC-KITCHENS [[2]](#References) and Ego4D [[1]](#References), has encouraged the research community to explore different opportunities for learning from egocentric videos, from the more traditional action recognition and anticipation tasks, to the use of natural language queries for video understanding.
A typical way for humans to understand what is happening in a video is to ask themselves questions under the form of natural language queries, like "Where was object <x> last seen?" or "Which objects did the user interact with?". Thus, the goal becomes to identify the segment of the video that allows the query to be answered. The use of natural language allows greater flexibility in the kinds of queries that can be made.


<div align="center" style="padding: 40px 0;">
  <img src="images/query_example.png" alt="ego4d_overview" width="450">
  <div style="font-size: 14px; color: gray; margin-top: 10px;">
    <em>Figure 2: An example of a query on the content of the video, expressed in natural language.</em>
    <br>
  </div>
</div>


## Methodology
### Dataset :
**• Ego4D** [[1]](#References): 3,000+ hours of egocentric video data.

**• EPIC-KITCHENS** [[2]](#References): Annotated kitchen activity videos.

## Notebooks

This project contains several notebooks for processing the Ego4D dataset and further analysis. Each notebook is designed for a specific task within the pipeline.

### **1. Query Selection Notebook (  /notebooks/Query_selection.ipynb  )**
**Purpose:** 
- Selects the top 50 video queries predicted using VSLNet model with non-shared Encoder from the Ego4D dataset based on Intersection over Union (IoU) scores between model predictions and ground truth annotations.

**Key Features:**
1. **Mapping Predictions to Video IDs:**
   - Matches `clip_uid` from the predictions with corresponding `video_uid` using the ground truth annotations.
   - Fixes errors in ground truth timestamps (e.g., negative values close to 0).

2. **Evaluate Predictions:**
   - Computes IoU for each query and ranks the predictions.
   - Evaluates performance using metrics like mean IoU and Recall@K (e.g., Recall@1, Recall@5).

3. **Select Top 50 Queries:**
   - Outputs the top 50 queries with the highest IoU scores.
   - Saves the results in `data/top_50_queries/top_queries.json`.

4. **Visualization:**
   - Plots the IoU distribution and query rankings for better understanding of model performance.

**Output:**
- A JSON file `top_queries.json` containing the selected queries, each with:
  - `video_id`
  - `clip_uid`
  - `query`
  - `ground_truth`
  - `IoU score`

---

### **2. Clip Extraction Notebook (  /notebooks/Clip_extraction.ipynb  )**
**Purpose:**
- Extracts specific video clips corresponding to the top 50 queries from the Ego4D dataset using ground truth intervals.

**Key Features:**
1. **AWS Environment Setup:**
   - Configures AWS CLI for accessing the Ego4D dataset hosted on S3.

2. **Download Manifest:**
   - Retrieves `manifest.csv`, which maps `video_id` to their respective S3 paths.

3. **Process Queries:**
   - Iterates over the top 50 queries from `top_queries.json`.
   - Downloads the corresponding videos and extracts clips using FFmpeg.

4. **Clip Storage:**
   - Saves extracted clips in `/content/extracted_clips`.
   - Compresses the folder into `/content/extracted_clips.zip` for easy download.

**Output:**
- Extracted clips saved in a compressed zip file for further analysis.



## References
[1] Grauman, Kristen, et al. "Ego4d: Around the world in 3,000 hours of egocentric video." Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition. 2022.
[2] Damen, Dima, et al. "Rescaling egocentric vision: Collection, pipeline and challenges for epic-kitchens-100." International Journal of Computer Vision (2022): 1-23.




