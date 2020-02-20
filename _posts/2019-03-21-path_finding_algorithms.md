--- 
layout: post  
current: post
title: 길찾기 알고리즘      
cover: /arongranberg.com/astar/resources/images/frontpage.jpg   
navigation: True
tags: technology
class: post-template
subclass: 'post tag-technology'       
date: 2019-03-11 00:00:01
author: tigim         
---  

Autonomous Navigation 부터 Fleet Management 시스템까지 패스파인딩 알고리즘이 안들어가는데 없다. 지금까지 검토한 내용 정리 해보자. 

Single-Agent Pathfindings     
==========================      

**[A* Algorithm]**

이 알고리즘이 소개된건 이미 몇 십년 전이지만, 여전히 대부분의 시스템에서 사용하는 길찾기 알고리즘은 A* 일 것이다. 동작의 핵심은 Heap Queue, 또는 Priority Queue을 사용한 DFS이다. 정렬을 위한 값/코스트는 (현재 위치부터 출발점 까지 거리 + 현재 위치부터 도착점 까지 거리)이며, 유클리디안 또는 맨하턴 방식으로 계산을 하는데, 당연히 맨하턴이 빠르겄지만서도 체감상 뭘 써도 차이는 없는 듯 하다. 

![](https://github.com/AtsushiSakai/PythonRoboticsGifs/raw/master/PathPlanning/AStar/animation.gif)

- [파이썬으로 작성된 코드](https://github.com/jfrascon/SLAM_AND_PATH_PLANNING_ALGORITHMS/blob/master/08-PATH_PLANNING/CODE/pp_01_e_astar_question.py)
- [한국어로 설명한 블로그](https://itmining.tistory.com/66)
  

**[Potential Field/Function]**  

A* 가 다좋은데, 문제가 하나 있다면 최적의 길찾기를 하다 보니, 벽에 딱 붙어가는 경우가 생긴다. 사람이 보기에는 장애물이 없다면 통로의 가운데 지나가는게 보기에 가장 좋기 때문이다. 그런 이유로 장애물 주위에 가중치를 부여해서 A* 의 코스트 값에 더해주면, 좀더 보기 좋은 길찾기가 가능해진다. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/nQtmUH3UCi4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>  

- [A* 와 결합된 Potential Function - 파이썬 코드](https://github.com/jfrascon/SLAM_AND_PATH_PLANNING_ALGORITHMS/blob/master/08-PATH_PLANNING/CODE/pp_01_f_astar_potential_function_question.py)  


**[dijkstra Algorithm]**

사용하는 내부 자료 구조 때문에 A* 보다 성능이 좋을수가 없으나, 분산 처리가 가능하다는 매력이 있다. 참고만 하자.  

![](https://github.com/AtsushiSakai/PythonRoboticsGifs/raw/master/PathPlanning/Dijkstra/animation.gif)  

<iframe width="560" height="315" src="https://www.youtube.com/embed/HFapeLxvdNg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

- [Dijkstra 소개 블로그](https://medium.com/basecs/finding-the-shortest-path-with-a-little-help-from-dijkstra-613149fbdc8e)  
- [CS553 Distributed Algorithms](https://www.cs.uic.edu/~ajayk/SelfStabilization.pdf)  
- [Distributed Shortest Paths Algorithms](https://www.cs.rit.edu/~ark/winter2012/730/team/1/presentation2.pdf)

Multi-Agent Pathfindings  
=========================    


**[WHCA* Algorithm]**

A* 에 시간 개념을 도입, 3D 환경에서 동작하게 만든 알고리즘. 적절한 크기의 타임 슬롯(Reservation Table)을 정하면, 무한 루프에 빠지는 일 없이 솔루션을 잘 찾아낸다. 속도는 코드 품질, 로봇의 수, 맵의 복잡도, 시스템 사양에 따라 틀리지만 대체로 좋은 성능을 보여준다. 40x40정도 크기이면 거의 실시간으로 동작한다.  

- [Complete Algorithms for Cooperative Pathfinding Problems, 2005년](https://pdfs.semanticscholar.org/1460/61be1affd4af17b8996f1d0316ad147368f5.pdf)
- [자바로 작성된 코드](https://github.com/igrek51/coop-pathfinder)

<iframe width="560" height="315" src="https://www.youtube.com/embed/DRx-17AHaw4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>  


**[ECBS]**  

제일 처음으로 검토한 알고리즘이며, 프로젝트 중반까지도 사용했었으나, 혼잡 상황에서 계산량 증가로 실시간 길찾기에 문제점이 많아 결국 폐기  

- [libMultiRobotPlanning - ECBS를 포함한 여러 알고리즘 있음](https://github.com/whoenig/libMultiRobotPlanning)


**[AA-SIPP]**  

SIPP를 기반으로 Advanced 알고리즘. 허나, 이 계열의 알고리즘은 혼잡 상황에서 로봇 간 Collision이 발생하기 때문에 실제 사용하지는 않았다.  
  
<iframe width="560" height="315" src="https://www.youtube.com/embed/1Jrye5S0ZV8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>   
  
- [Any-Angle Pathfinding for Multiple Agents Based on SIPP Algorithm, 2017년](https://arxiv.org/pdf/1703.04159.pdf)
- [C++ 코드](https://github.com/PathPlanning/AA-SIPP-m)



Reference  
=========  

- [Python Robotics, 최고의 로봇 관련 파이썬 예제코드](https://github.com/AtsushiSakai/PythonRobotics)
- [SLAM 및 Path-Planning MOOC 강좌](https://github.com/jfrascon/SLAM_AND_PATH_PLANNING_ALGORITHMS/tree/master/08-PATH_PLANNING/CODE)  
- [Path Planning for Robotic Mobile Fulfillment Systems](https://www.groundai.com/project/path-planning-for-robotic-mobile-fulfillment-systems/1#bib.bib24)  
- [Gazebo로 멀티 로봇 시뮬레이션 구축](https://github.com/PathPlanning/MultiRobotPathFinding-ROS-Gazebo-Demo)