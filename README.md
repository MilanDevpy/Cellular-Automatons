# Cellular Automatons
**RUN WITH --release FLAG !!!**    
If you have a black screen, juste press space or set to false `WAIT_FOR_SIGNAL` in config.rs
> A cellular automaton (pl. cellular automata, abbrev. CA) is a discrete model of computation studied in automata theory. Cellular automata are also called cellular spaces, tessellation automata, homogeneous structures, cellular structures, tessellation structures, and iterative arrays. Cellular automata have found application in various areas, including physics, theoretical biology, and microstructure modeling.  
[_Wikipedia_](https://en.wikipedia.org/wiki/Cellular_automaton)

didn't understand a shit ? Me too lol, all u need to know is that it's FUN)
In other words, each cell (or pixel if u want) looks at it's neighbours and will adujst ajust it's state. 
Actually there are only 2 CA, Life and Cyclic. If you want to understand what's the difference you can read [this paper](https://web.archive.org/web/20180122193053/http://www.mirekw.com/ca/index.html) (I love Internet Archive xD)
You can play with the parameters in the config.rs, below some working exemples :
## Life
`pub const SIMULATION_TYPE: SimulationType = SimulationType::Life;`

**Conway GOF:**
*The original GOF*
```rust
const CELL_TYPE: CellType = CellType {
    b: &[3],
    s: &[2,3],
    color: WHITE,
};
```
**Coagulations:**
*It stabilizes with a majority of living cells, pretty cool*
```rust
const CELL_TYPE: CellType = CellType {
    b: &[3, 7, 8],
    s: &[2, 3, 5, 6, 7, 8],
    color: YELLOW,
};
```

**1/1**
*Very impressive for only one parameter, but try it in Full Circle*

```rust
const CELL_TYPE: CellType = CellType {
    b: &[1],
    s: &[1],
    color: RED,
};
```
**Maze**
*One of my favorites*
```rust
const CELL_TYPE: CellType = CellType {
    b: &[3],
    s: &[1, 2, 3, 4, 5],
    color: BLUE,
};
```
## Cyclic
`pub const SIMULATION_TYPE: SimulationType = SimulationType::Cyclic;`  


**Lava lamp**  
*The perfect automaton*  


<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/dbea9af4-557f-4348-9ee6-32e4ccd750e6" />  

```rust
pub const CYCLIC_PATTERN: CyclicPattern = CyclicPattern {
    pattern: SearchPattern::Classic,
    search_distance: 2,
    states: 3,
    neighbours: 10,
    color_scheme: CyclicColors::Random,
};
```

**313**  
*very goofy*  


<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/e8af0b74-200f-4e03-a326-94126b1e9519" />

```rust
pub const CYCLIC_PATTERN: CyclicPattern = CyclicPattern {
    pattern: SearchPattern::Classic,
    search_distance: 2,
    states: 3,
    neighbours: 10,
    color_scheme: CyclicColors::Random,
};
```


**Vorace**  
*Finded it randomly, pretty cool ngl*  


<img width="140" height="140" alt="image" src="https://github.com/user-attachments/assets/047301bc-6155-4238-b872-89c3c00dc80e" /><img width="140" height="140" alt="image" src="https://github.com/user-attachments/assets/6b14c8fd-3e8f-464c-ad50-fec6512082da" /><img width="140" height="140" alt="image" src="https://github.com/user-attachments/assets/964ee836-e98a-4899-8f6d-f4bfec38684f" />




```rust
pub const CYCLIC_PATTERN: CyclicPattern = CyclicPattern {
    pattern: SearchPattern::Classic,
    search_distance: 1,
    states: 31,
    neighbours: 1, // yeah it's stupid but it's MINIMAL neighbours to change
    color_scheme: CyclicColors::Random,
};
```
