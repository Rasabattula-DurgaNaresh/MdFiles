# 300 Java 8 Stream Interview Questions

A comprehensive list of **Java 8 Stream interview questions** used in backend developer interviews (2–10 years experience).

---

# Section 1 — Basic Stream Concepts (1–40)

1. What is a Stream in Java 8?
2. Difference between Collection and Stream?
3. What are the key features of Java Streams?
4. What is lazy evaluation in streams?
5. What is the difference between intermediate and terminal operations?
6. Name common intermediate operations in streams.
7. Name common terminal operations in streams.
8. What is the use of `map()`?
9. What is the use of `filter()`?
10. What is `flatMap()`?
11. Difference between `map()` and `flatMap()`?
12. What does `forEach()` do?
13. What is `collect()`?
14. What is `reduce()`?
15. What is `Optional` in Java Streams?
16. What is the purpose of `distinct()`?
17. What does `limit()` do?
18. What does `skip()` do?
19. What does `sorted()` do?
20. How do you convert a list to a stream?
21. How do you convert an array to a stream?
22. How do you create an infinite stream?
23. What is `Stream.iterate()`?
24. What is `Stream.generate()`?
25. Difference between sequential and parallel streams?
26. What is `parallelStream()`?
27. How does stream pipeline work?
28. What is short-circuiting in streams?
29. What is a stateless lambda?
30. What is a stateful lambda?
31. What is the difference between `findFirst()` and `findAny()`?
32. What is `allMatch()`?
33. What is `anyMatch()`?
34. What is `noneMatch()`?
35. What happens if a stream is reused?
36. Can streams modify source collections?
37. What is the difference between `peek()` and `map()`?
38. What is the difference between `count()` and `collect()`?
39. What are primitive streams?
40. What are `IntStream`, `LongStream`, and `DoubleStream`?

---

# Section 2 — Intermediate Operations (41–90)

41. How does `filter()` work internally?
42. How does `map()` transform data?
43. What happens when `distinct()` is used?
44. How does `sorted()` behave without a comparator?
45. How does `sorted(Comparator)` work?
46. What is the cost of `distinct()`?
47. What happens when multiple filters are chained?
48. What does `peek()` help with?
49. When should `flatMap()` be used?
50. How to flatten a list of lists?
51. How to flatten a stream of arrays?
52. Can intermediate operations modify objects?
53. Can streams contain null values?
54. What happens if null is passed to a stream operation?
55. How to debug stream pipelines?
56. What happens when `limit()` is used with infinite streams?
57. What happens when `skip()` exceeds list size?
58. Can you sort a stream twice?
59. What happens when `distinct()` is used after `sorted()`?
60. Can intermediate operations be parallelized?
61. What happens if `peek()` modifies data?
62. What are side effects in streams?
63. What is a non-interfering function?
64. What is a stateless function?
65. Why are stateless functions recommended?
66. Can `filter()` change object fields?
67. What is pipeline fusion?
68. How many times is a stream traversed?
69. Can you create custom intermediate operations?
70. What is the order of execution in stream pipelines?
71. Can intermediate operations throw exceptions?
72. What happens when exceptions occur in streams?
73. Can streams be nested?
74. What is the complexity of stream operations?
75. What happens when `limit()` is used after `sorted()`?
76. What happens when `sorted()` is used after `limit()`?
77. How does `flatMap()` improve performance?
78. Can `map()` return null values?
79. Can `filter()` remove duplicates?
80. Can streams operate on primitive arrays?
81. What happens if comparator is inconsistent?
82. How do streams handle ordering?
83. Can you preserve order in parallel streams?
84. What does `unordered()` do?
85. When should `unordered()` be used?
86. How does `distinct()` work in parallel streams?
87. What is a spliterator?
88. How does spliterator support streams?
89. What is stream source?
90. Can streams operate on I/O channels?

---

# Section 3 — Terminal Operations (91–140)

91. What does `collect()` do?
92. What is `Collectors.toList()`?
93. What is `Collectors.toSet()`?
94. What is `Collectors.toMap()`?
95. What does `reduce()` do?
96. Difference between `reduce()` and `collect()`?
97. What is mutable reduction?
98. What is immutable reduction?
99. What does `count()` do?
100. What does `min()` do?
101. What does `max()` do?
102. What does `findFirst()` return?
103. What does `findAny()` return?
104. What happens if stream is empty?
105. What is `Optional.get()` risk?
106. What is `Optional.orElse()`?
107. What is `Optional.orElseGet()`?
108. What is `Optional.orElseThrow()`?
109. What happens if `reduce()` has no identity?
110. What is combiner function?
111. What is accumulator function?
112. What happens when reduce is parallel?
113. What does `forEachOrdered()` do?
114. Difference between `forEach()` and `forEachOrdered()`?
115. Can terminal operations be chained?
116. What happens if terminal operation is missing?
117. Can streams have multiple terminal operations?
118. What does `joining()` collector do?
119. What does `averagingInt()` do?
120. What does `summarizingInt()` do?
121. What does `counting()` collector do?
122. What does `mapping()` collector do?
123. What does `collectingAndThen()` do?
124. What is `partitioningBy()`?
125. What is `groupingBy()`?
126. What is downstream collector?
127. What is `reducing()` collector?
128. What happens if duplicate keys exist in `toMap()`?
129. How to handle duplicate keys in map collectors?
130. What is merge function in `toMap()`?
131. What does `teeing()` collector do?
132. Can collectors be parallelized?
133. What is immutable collector?
134. Can streams write to files?
135. Can streams read from files?
136. What is `Files.lines()`?
137. What is `Stream.of()`?
138. What does `Stream.empty()` do?
139. What happens after terminal operation finishes?
140. What happens if stream pipeline fails?

---

# Section 4 — Coding Problems (141–220)

141. Find duplicate elements in a list.
142. Find first non-repeating character.
143. Find second highest number.
144. Find max value in list.
145. Find min value in list.
146. Remove duplicates from list.
147. Find even numbers from list.
148. Find odd numbers from list.
149. Find sum of numbers.
150. Find average of numbers.
151. Find numbers greater than 10.
152. Find common elements between two lists.
153. Find longest string in list.
154. Find shortest string.
155. Find palindrome strings.
156. Convert list to map.
157. Convert map to list.
158. Group employees by department.
159. Count employees by department.
160. Find highest salary employee.
161. Find second highest salary employee.
162. Find top 3 salaries.
163. Sort employees by salary.
164. Sort employees by name.
165. Find duplicate characters in string.
166. Count characters in string.
167. Reverse words in sentence.
168. Find frequency of words.
169. Find most frequent element.
170. Find least frequent element.
171. Partition numbers into even/odd.
172. Merge two lists.
173. Merge two maps.
174. Flatten list of lists.
175. Flatten nested objects.
176. Find kth largest element.
177. Find kth smallest element.
178. Convert stream to array.
179. Convert array to stream.
180. Find numbers divisible by 3.
181. Find numbers divisible by 5.
182. Remove null values from list.
183. Replace null values.
184. Find duplicate employees.
185. Remove duplicate employees.
186. Sort map by key.
187. Sort map by value.
188. Find employees older than 30.
189. Find employees with salary > 50k.
190. Find department with highest salary.
191. Find average salary by department.
192. Find total salary by department.
193. Find youngest employee.
194. Find oldest employee.
195. Find employees joined last year.
196. Find employees joined this month.
197. Count active users.
198. Find inactive users.
199. Find longest word in file.
200. Find top 10 words in file.
201. Generate Fibonacci series.
202. Generate random numbers.
203. Find duplicates in array.
204. Convert list of strings to uppercase.
205. Convert list to lowercase.
206. Filter strings starting with A.
207. Filter strings ending with Z.
208. Find strings containing substring.
209. Find unique characters in string.
210. Count vowels in string.
211. Count consonants in string.
212. Find maximum length string.
213. Find minimum length string.
214. Find median value.
215. Find product of numbers.
216. Find factorial using streams.
217. Find squares of numbers.
218. Find cubes of numbers.
219. Remove negative numbers.
220. Find positive numbers.

---

# Section 5 — Advanced Stream Interview Questions (221–300)

221. What is stream pipeline optimization?
222. What is stream fusion?
223. What is internal iteration?
224. What is external iteration?
225. How do streams improve performance?
226. When should streams not be used?
227. What are stream performance pitfalls?
228. How do parallel streams split data?
229. What is ForkJoinPool?
230. How does parallel stream use ForkJoinPool?
231. What are thread safety concerns in streams?
232. What are race conditions in streams?
233. Can streams modify shared state?
234. What is stream laziness?
235. How does short-circuiting work?
236. What is memory overhead of streams?
237. What is difference between loop vs stream?
238. Are streams faster than loops?
239. When should loops be preferred?
240. Can streams cause memory leaks?
241. How to profile stream performance?
242. What is spliterator characteristic?
243. What is ORDERED spliterator?
244. What is SIZED spliterator?
245. What is DISTINCT spliterator?
246. What is IMMUTABLE spliterator?
247. What is CONCURRENT spliterator?
248. How to create custom collector?
249. What is Collector interface?
250. What are collector components?
251. What is supplier in collector?
252. What is accumulator in collector?
253. What is combiner in collector?
254. What is finisher in collector?
255. What are collector characteristics?
256. How to build immutable collectors?
257. What is `Collectors.groupingByConcurrent()`?
258. When to use concurrent collectors?
259. What is stream backpressure?
260. How to debug parallel streams?
261. What are side effects in parallel streams?
262. How to avoid race conditions?
263. How to test stream pipelines?
264. How to mock streams in tests?
265. How to benchmark stream performance?
266. What are stream best practices?
267. What are stream anti-patterns?
268. When should flatMap be avoided?
269. How to optimize nested streams?
270. How to process huge datasets with streams?
271. How to stream database results?
272. How to stream large files?
273. How to handle exceptions in streams?
274. How to implement retry logic in streams?
275. How to log stream operations?
276. How to build reusable stream utilities?
277. What is stream collector composition?
278. How to chain collectors?
279. What is stream reduction pattern?
280. What is map-reduce pattern?
281. How to parallelize reductions?
282. What is associative reduction?
283. Why must reduction be associative?
284. What is identity value in reduce?
285. What are deterministic stream results?
286. What are non-deterministic results?
287. What is order-sensitive stream operation?
288. What is order-insensitive stream operation?
289. How to maintain order in parallel streams?
290. What is `StreamSupport`?
291. How to create custom streams?
292. How to implement custom spliterator?
293. What is stream cancellation?
294. How to short-circuit parallel streams?
295. What is stream batching?
296. What is windowing in streams?
297. How to handle backpressure?
298. What are stream design patterns?
299. How to build high-performance pipelines?
300. What are the best practices for Java Streams?

---

# End

Practice these questions to master **Java 8 Streams for backend interviews**.
