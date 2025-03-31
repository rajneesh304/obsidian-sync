You are given an array `prerequisites` where `prerequisites[i] = [a, b]` indicates that you **must** take course `b` first if you want to take course `a`.

- For example, the pair `[0, 1]`, indicates that to take course `0` you have to first take course `1`.

There are a total of `numCourses` courses you are required to take, labeled from `0` to `numCourses - 1`.

Return a valid ordering of courses you can take to finish all courses. If there are many valid answers, return **any** of them. If it's not possible to finish all courses, return an **empty array**.


- There can be multiple topological orderings for one graph.
- A node can have 3 states :
- 