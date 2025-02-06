# Philosophers
![philosophers Small](https://github.com/user-attachments/assets/79fe02aa-e86e-4a80-8cb2-68a6e57c5ea4)

## Description
Philosophers is a project that introduces the basics of multithreading and synchronization using mutexes in C. The goal is to simulate the classic Dining Philosophers problem using threads and mutexes while avoiding common concurrency issues such as deadlocks and data races.

## Project Overview
In this simulation:
- Several philosophers sit around a circular table with a bowl of spaghetti.
- Each philosopher alternates between eating, sleeping, and thinking.
- To eat, a philosopher must pick up both their left and right forks (mutexes).
- If a philosopher does not eat within `time_to_die` milliseconds, they die, ending the simulation.
- The simulation ends either when a philosopher dies or when all philosophers have eaten a specified number of times (if `number_of_times_each_philosopher_must_eat` is provided as an argument).

## Features
- Multithreading with `pthread`
- Mutex synchronization to avoid race conditions
- Precise timing using `gettimeofday` and `usleep`
- Proper memory management to avoid leaks

## Usage
### Compilation
To compile the project, run:
```sh
make
```
This will generate an executable named `philo`.

To clean up compiled files:
```sh
make clean
```
To remove compiled files and the executable:
```sh
make fclean
```
To recompile everything:
```sh
make re
```

### Running the Program
The program takes the following arguments:
```sh
./philo number_of_philosophers time_to_die time_to_eat time_to_sleep [number_of_times_each_philosopher_must_eat]
```
- `number_of_philosophers`: The number of philosophers (and forks).
- `time_to_die`: Time (in milliseconds) after which a philosopher dies if they don’t eat.
- `time_to_eat`: Time (in milliseconds) it takes for a philosopher to eat.
- `time_to_sleep`: Time (in milliseconds) a philosopher spends sleeping.
- `number_of_times_each_philosopher_must_eat` (optional): If provided, the simulation ends when all philosophers have eaten this many times.

#### Example
```sh
./philo 5 800 200 200
```
This runs a simulation with:
- 5 philosophers
- 800ms time to die
- 200ms time to eat
- 200ms time to sleep

## Rules & Constraints
- **Global variables are forbidden.**
- **Each philosopher is a separate thread.**
- **Each fork is protected by a mutex.**
- **Philosophers must not print overlapping messages.**
- **A message announcing a philosopher's death must be displayed within 10ms of actual death.**
- **The program must not have data races.**

## Allowed Functions
The following functions are allowed:
- `memset`, `printf`, `malloc`, `free`, `write`, `usleep`, `gettimeofday`
- `pthread_create`, `pthread_detach`, `pthread_join`
- `pthread_mutex_init`, `pthread_mutex_destroy`, `pthread_mutex_lock`, `pthread_mutex_unlock`

## Bonus
Although I haven’t done it, the bonus version implements the simulation using processes and semaphores instead of threads and mutexes.
