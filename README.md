# Php-GoalSeek

- Php function to simulate Goal Seek from libre office using the Regula Falsi method.
- In most cases the result is equal of the Excel formula. Because the Excel do not show what formula are used in goal seak we need to use the similar function in Libre Office.

- Install
 ```bash
 composer require kidjapa/php-goalseek
 ```


## In Libre office

- Function in archive: core/sc/source/coredata/dcoumen4.cxx

```c++
bool ScDocument::Solver(SCCOL nFCol, SCROW nFRow, SCTAB nFTab,
                        SCCOL nVCol, SCROW nVRow, SCTAB nVTab,
                        const OUString& sValStr, 
                        double& nX
                        )
```

## Sample

```php
$goalSeek = new SolveGoalSeek();

$getValue = 0;

$getValue = $goalSeek->seekGoal(
    function($value, $data){
        return sqrt($value);
    },
    16,  // The Actual Value
    20   // The Goal Value
);

echo "------------- results ------------- \n";
echo "Result: ".$getValue."\n"; // Expect: 400
```
