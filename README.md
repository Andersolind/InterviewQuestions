# Interview Questions

## Event Loop

```
How do Event loops work?

Call Stack:

JavaScript uses a call stack to keep track of the currently executing function (where the program is in its execution).
Callback Queue:
Asynchronous operations, such as I/O operations or timers, are handled by the browser or Node.js runtime. When these operations are complete, corresponding functions (callbacks) are placed in the callback queue.

Event Loop:

The event loop continuously checks the call stack and the callback queue. If the call stack is empty, it takes the first function from the callback queue and pushes it onto the call stack for execution.
Execution:

The function on top of the call stack is executed. If this function contains asynchronous code, it might initiate further asynchronous operations.
Callback Execution:
When an asynchronous operation is complete, its callback is placed in the callback queue.
Repeat:

The event loop continues this process, ensuring that the call stack is always empty before taking the next function from the callback queue.
Example: In this example, a JavaScript script demonstrates synchronous blocking behavior. It starts by logging “Before delay,” then uses a function delayBySeconds to create a delay of 5 seconds using a busy-wait loop. The script then logs “After delay” after the 5-second delay completes.
```

## Observables vs Promises

```
Promises are suitable for single asynchronous operations like fetching data from an API.
Observables are ideal for handling streams of data, such as user input, WebSocket events, or HTTP responses,
where multiple values might be emitted over time.
```
## Plus and minus hacker rank test 

```
import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.function.*;
import java.util.regex.*;
import java.util.stream.*;
import static java.util.stream.Collectors.joining;
import static java.util.stream.Collectors.toList;

class Result {

    /*
     * Complete the 'plusMinus' function below.
     *
     * The function accepts INTEGER_ARRAY arr as parameter.
     */

    public static void plusMinus(List<Integer> arr) {
    // Write your code here
    float positiveCount = 0, 
           negativeCount = 0, 
           zeroCount = 0, 
           n = 0;

            for (int i = 0; i < arr.size(); i++)
            {
                n++;
                if (arr.get(i) > 0)
                {
                    positiveCount++;
                }
                else if (arr.get(i) < 0)
                {
                    negativeCount++;
                }
                else {
                    zeroCount++;
                }

            }
            
            System.out.println(String.format("%.6f", positiveCount / n));
            System.out.println(String.format("%.6f", negativeCount / n));
            System.out.println(String.format("%.6f", zeroCount / n));
            
           

    }

}

public class Solution {
    public static void main(String[] args) throws IOException {
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));

        int n = Integer.parseInt(bufferedReader.readLine().trim());

        List<Integer> arr = Stream.of(bufferedReader.readLine().replaceAll("\\s+$", "").split(" "))
            .map(Integer::parseInt)
            .collect(toList());

        Result.plusMinus(arr);

        bufferedReader.close();
    }
}

```

```
-- miniMaxSum test 
import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.function.*;
import java.util.regex.*;
import java.util.stream.*;
import static java.util.stream.Collectors.joining;
import static java.util.stream.Collectors.toList;

class Result {

    /*
     * Complete the 'miniMaxSum' function below.
     *
     * The function accepts INTEGER_ARRAY arr as parameter.
     */

    public static void miniMaxSum(List<Integer> arr) {
    // Write your code here
        Long min = 0L;
        Long max = 0L;
        Long total = 0L;
        for( Integer number : arr ){
            total+= Long.valueOf( number );

            if( number < min || min == 0 ){
                min= Long.valueOf(number);
            }
            if( number > max ){
                max= Long.valueOf(number);
            }
        }

        System.out.printf("%d %d", (total - max), (total - min));
    }

}

public class Solution {
    public static void main(String[] args) throws IOException {
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));

        List<Integer> arr = Stream.of(bufferedReader.readLine().replaceAll("\\s+$", "").split(" "))
            .map(Integer::parseInt)
            .collect(toList());

        Result.miniMaxSum(arr);

        bufferedReader.close();
    }
}

```
```
Java script

'use strict';

process.stdin.resume();
process.stdin.setEncoding('utf-8');

let inputString = '';
let currentLine = 0;

process.stdin.on('data', function(inputStdin) {
    inputString += inputStdin;
});

process.stdin.on('end', function() {
    inputString = inputString.split('\n');

    main();
});

function readLine() {
    return inputString[currentLine++];
}

/*
 * Complete the 'plusMinus' function below.
 *
 * The function accepts INTEGER_ARRAY arr as parameter.
 */

function plusMinus(arr) {
    // Write your code here
    let positive = arr.filter(number => number > 0).length / arr.length;
    let negative = arr.filter(number => number < 0).length / arr.length;;
    let zeronums = arr.filter(number => number == 0).length / arr.length;;
    return console.log(positive.toFixed(6) + '\n' + negative.toFixed(6) + '\n' + zeronums.toFixed(6))
}

function main() {
    const n = parseInt(readLine().trim(), 10);

    const arr = readLine().replace(/\s+$/g, '').split(' ').map(arrTemp => parseInt(arrTemp, 10));

    plusMinus(arr);
}

```
```
'use strict';

process.stdin.resume();
process.stdin.setEncoding('utf-8');

let inputString = '';
let currentLine = 0;

process.stdin.on('data', function(inputStdin) {
    inputString += inputStdin;
});

process.stdin.on('end', function() {
    inputString = inputString.split('\n');

    main();
});

function readLine() {
    return inputString[currentLine++];
}

/*
 * Complete the 'miniMaxSum' function below.
 *
 * The function accepts INTEGER_ARRAY arr as parameter.
 */

function miniMaxSum(arr) {
    // Write your code here
 console.log(`${arr.sort().slice(0,-1)
  .reduce((a,b)=>a+b)} ${arr.sort()
  .slice(1).reduce((a,b)=>a+b)}`)
}

function main() {

    const arr = readLine().replace(/\s+$/g, '').split(' ').map(arrTemp => parseInt(arrTemp, 10));

    miniMaxSum(arr);
}

```
```
type script

'use strict';

process.stdin.resume();
process.stdin.setEncoding('utf-8');

let inputString: string = '';
let inputLines: string[] = [];
let currentLine: number = 0;

process.stdin.on('data', function(inputStdin: string): void {
    inputString += inputStdin;
});

process.stdin.on('end', function(): void {
    inputLines = inputString.split('\n');
    inputString = '';

    main();
});

function readLine(): string {
    return inputLines[currentLine++];
}

/*
 * Complete the 'plusMinus' function below.
 *
 * The function accepts INTEGER_ARRAY arr as parameter.
 */

function plusMinus(arr: number[]): void {
    // Write your code here
 var n = arr.length; 
    //console.log(n)
    //console.log(arr)
    var numberOfPositiveValue = 0
    var numberOfNegativeValue = 0
    var numberOfZeroValue = 0

    for (var i = 0; i < n; i++) {
        if (arr[i] > 0) {
            numberOfPositiveValue = numberOfPositiveValue + 1
        }
        if (arr[i] < 0) {
            numberOfNegativeValue = numberOfNegativeValue + 1
        }
        if (arr[i] === 0) {
            numberOfZeroValue = numberOfZeroValue + 1
        }
    }

    var numberOfPositiveValueAfterMultipleN = numberOfPositiveValue / n
    var numberOfNegativeValueAfterMultipleN = numberOfNegativeValue / n
    var numberOfZeroValueAfterMultipleN = numberOfZeroValue / n

    console.log(numberOfPositiveValueAfterMultipleN.toFixed(6))
    console.log(numberOfNegativeValueAfterMultipleN.toFixed(6))
    console.log(numberOfZeroValueAfterMultipleN.toFixed(6))

}

function main() {
    const n: number = parseInt(readLine().trim(), 10);

    const arr: number[] = readLine().replace(/\s+$/g, '').split(' ').map(arrTemp => parseInt(arrTemp, 10));

    plusMinus(arr);
}
```
##  undirected graph graph

```
class Vertex<T> {
    value: T;
    constructor(value: T) {
        this.value = value;
    }
}

class Edge<T> {
    start: Vertex<T>;
    end: Vertex<T>;
    weight: number; // If the graph is weighted

    constructor(start: Vertex<T>, end: Vertex<T>, weight: number = 1) {
        this.start = start;
        this.end = end;
        this.weight = weight;
    }
}

class Graph<T> {
    vertices: Vertex<T>[];
    edges: Edge<T>[];

    constructor() {
        this.vertices = [];
        this.edges = [];
    }

    addVertex(value: T): Vertex<T> {
        const vertex = new Vertex(value);
        this.vertices.push(vertex);
        return vertex;
    }

    addEdge(vertex1: Vertex<T>, vertex2: Vertex<T>, weight: number = 1) {
        const edge = new Edge(vertex1, vertex2, weight);
        this.edges.push(edge);
        // For an undirected graph, we add edges in both directions
        const reverseEdge = new Edge(vertex2, vertex1, weight);
        this.edges.push(reverseEdge);
    }

    getNeighbors(vertex: Vertex<T>): Vertex<T>[] {
        const neighbors: Vertex<T>[] = [];
        this.edges.forEach(edge => {
            if (edge.start === vertex) {
                neighbors.push(edge.end);
            }
        });
        return neighbors;
    }

    printGraph(): void {
        console.log("Vertices:");
        this.vertices.forEach(vertex => {
            console.log(vertex.value);
        });

        console.log("Edges:");
        this.edges.forEach(edge => {
            console.log(`${edge.start.value} <-> ${edge.end.value} (Weight: ${edge.weight})`);
        });
    }
}

// Example usage:

// Create a graph
const graph = new Graph<number>();

// Add vertices
const vertex1 = graph.addVertex(1);
const vertex2 = graph.addVertex(2);
const vertex3 = graph.addVertex(3);

// Add edges
graph.addEdge(vertex1, vertex2);
graph.addEdge(vertex2, vertex3);
graph.addEdge(vertex3, vertex1);

// Print the graph
graph.printGraph();

// Get neighbors of a vertex
const neighborsOfVertex1 = graph.getNeighbors(vertex1);
console.log(`Neighbors of vertex 1: ${neighborsOfVertex1.map(v => v.value).join(', ')}`);
```