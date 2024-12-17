# Natural Language Queries in Egocentric Videos

## Table of Contents
- [Project Overview](#project-overview)
- [Methodology](#methodology)
    - [Dataset](#dataset)
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

## References
[1] Grauman, Kristen, et al. "Ego4d: Around the world in 3,000 hours of egocentric video." Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition. 2022.
[2] Damen, Dima, et al. "Rescaling egocentric vision: Collection, pipeline and challenges for epic-kitchens-100." International Journal of Computer Vision (2022): 1-23.




