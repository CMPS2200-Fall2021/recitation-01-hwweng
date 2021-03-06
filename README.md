# CMPS 2200  Recitation 01

**Name (Team Member 1):**____Haowen Weng_____________________  
**Name (Team Member 2):**____Yuxuan Zhang_____________________

In this recitation, we will investigate asymptotic complexity. Additionally, we will get familiar with the various technologies we'll use for collaborative coding.

To complete this recitation, follow the instructions in this document. Some of your answers will go in this file, and others will require you to edit `main.py`.


## Setup
- Login to Github.
- Click on the assignment link sent through canvas and accept the assignment.
- Click on your personal github repository for the assignment (e.g., https://github.com/tulane-cmps2200/recitation-01-your_username).
- [Clone](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository-from-github/cloning-a-repository) the repository to your local device
- Complete the lab task
- [Add, commit, and push](https://docs.github.com/en/github/managing-files-in-a-repository/managing-files-using-the-command-line/adding-a-file-to-a-repository-using-the-command-line) your completed lab back up to GitHub.
  - You will need to issue `git add` for all files that you have modified, e.g., `main.py`, `README.md`, and any others that you modify as well.
  - For example, on the command line, in the same directory as your cloned lab:
```
$ git add main.py
$ git commit -m "Implement Required Functions"
$ git push origin main
```

You'll work with a partner to complete this recitation. You will be able to code together in the same `repl.it` instance. You can choose whose repl.it instance you will share. This person will click the "Share" button in their repl.it instance and email the lab partner.

## Turning in your work
- Only one team member needs to push your completed lab to github.
- In the README.md file, include the name of the team members.


## Comparing search algorithms

We'll compare the running times of `linear_search` and `binary_search` empirically.

- [ ] 1. In `main.py`, the implementation of `linear_search` is already complete. Your task is to implement `binary_search`. Implement a recursive solution using the helper function `_binary_search`.

- [ ] 2. Test that your function is correct by calling from the command-line `pytest main.py::test_binary_search`

- [ ] 3. Write at least two additional test cases in `test_binary_search` and confirm they pass.

- [ ] 4. Describe the worst case input value of `key` for `linear_search`? for `binary_search`?
    For linear search algorithm, the worst case is that after seaching every index of the list, either the last one was the element looking for or the element was not in the lsit and returns -1.
    For binary search algorithm, the worst case would be like: the input key is either first/last element of the list or no exists in the list.

- [ ] 5. Describe the best case input value of `key` for `linear_search`? for `binary_search`?
    For linear search, the best case is that the first element of the list is the one we looked for.
    For binary search, the best case is that the one in the mniddle of the list is the element we looked for.

- [ ] 6. Complete the `time_search` function to compute the running time of a search function. Note that this is an example of a "higher order" function, since one of its parameters is another function.

- [ ] 7. Complete the `compare_search` function to compare the running times of linear search and binary search. Confirm the implementation by running `pytest main.py::test_compare_search`, which contains some simple checks.

- [ ] 8. Call `print_results(compare_search())` and paste the results here:
|            n |   linear |   binary |
|--------------|----------|----------|
|       10.000 |    0.000 |    0.000 |
|      100.000 |    0.000 |    0.000 |
|     1000.000 |    0.000 |    0.000 |
|    10000.000 |    0.001 |    0.000 |
|   100000.000 |    0.013 |    0.000 |
|  1000000.000 |    0.209 |    0.000 |
| 10000000.000 |    2.120 |    0.000 |


- [ ] 9. The theoretical worst-case running time of linear search is $O(n)$ and binary search is $O(log_2(n))$. Do these theoretical running times match your empirical results? Why or why not?
  Yes, for each cycle of a binary search, it eliminates half of the remaining elements. The data from previous tests also shows the same result.

- [ ] 10. Binary search assumes the input list is already sorted. Assume it takes $\Theta(n^2)$ time to sort a list of length $n$. Suppose you know ahead of time that you will search the same list $k$ times.
  + What is worst-case complexity of searching a list of $n$ elements $k$ times using linear search?
        O(n) * k
  + For binary search?
        Theta(n^2) + k * O(log_2(n))
  + For what values of $k$ is it more efficient to first sort and then use binary search versus just using linear search without sorting?
        When the size of the list is large and k is small enough, binary search may takes more time than linear search since it need to sort the list first. However, with the increase of n, the increment of time by using linear search increases faster than binary search.
