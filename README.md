# TV Show Time Tracker

The **TV Show Time Tracker** consists of two components designed to calculate and compare the total runtime of different TV shows.

### I. `GetTvShowTotalLength` - C# Console Application

This application retrieves the total runtime of a given TV show by querying the [TVMaze API](https://www.tvmaze.com/api). It processes all episodes of the show, summing up the runtimes of aired episodes while skipping unaired ones.

Features:
- If the TV show cannot be found, the application exits with exit code 10.
- If multiple shows match the provided name, the most recent one is selected.
- The total runtime is output as a single number in minutes.
- Episodes without a runtime are ignored.

Usage:
```sh
$ ./GetTvShowTotalLength "The Office"
6060
```

### II. tv-time.py - Python Script

The script determines which TV show from a given list takes the least and the most time to watch. It executes `GetTvShowTotalLength` for each TV show concurrently.

Features:
- Accepts a list of TV show names via standard input.
- Uses the `GET_TVSHOW_TOTAL_LENGTH_BIN` environment variable to locate the GetTvShowTotalLength binary.
- Executes all TV show queries in parallel.
- Identifies the shortest and longest show in terms of total runtime.
- If `GetTvShowTotalLength` fails for any show, an error message is printed to standard error.

Input Format (tv-shows.txt):
```
The Office
Breaking Bad
House
The End of the F***ing World
Rick and Morty
Grey's Anatomy
CSI: Vegas
Buffy, the Vampire Slayer
3%
Sliiiders
Disney's Adventures of the Gummi Bears
That '70s Show
```

Example Execution:
```sh
$ ./tv-time.sh <tv-shows.txt
The shortest show: Firefly (360h 25m)
The longest show: The Bold and the Beautiful (10000h 20m)
```

If a show cannot be retrieved:
```
Could not get info for Sliiiders.
```
