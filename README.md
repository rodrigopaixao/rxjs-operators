# RXJS Operators

```
import { of, interval, from, timer } from 'rxjs'; 
import { map, mergeMap, switchMap } from 'rxjs/operators';

// map operator example

console.log('map ----------------------------');

const mapSource = of('Original String').pipe(
  map(string => `Modified String!`)
);

mapSource.subscribe(x => console.log(x));

// switchMap operator example

console.log('switchMap ----------------------------');

const switched = of(1, 2, 3)
  .pipe(
    switchMap((x: number) => of(x, x * 2)
      .pipe(
        map(param => `Value ${param}`)
      )
    )
);

switched.subscribe(x => console.log(x));

// mergeMap operator

console.log('mergeMap ----------------------------');

const letters = of('a', 'b', 'c');

const result = letters.pipe(
  mergeMap(x => from([1,2,3]).pipe(map(i => x+i))),
);

result.subscribe(x => console.log(x));
```