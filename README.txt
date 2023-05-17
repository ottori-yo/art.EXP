This code will print all the possible combinations of 420 (1* artifact) and 2500 (3* EXP.flask) values that add up to a number between 16200 and 16400 without going over the target number and also list the resulting sum of the selected possible combinations. 16300 is the value required to reach level 4.


This is .sh script for Windows PowerShell:

$a = @(420, 2500)
$n = 16300

for ($i = 1; $i -le $n/$a[0]; $i++) {
    for ($j = 1; $j -le $n/$a[1]; $j++) {
        if ($i*$a[0] + $j*$a[1] -gt 16200 -and $i*$a[0] + $j*$a[1] -lt 16400 -and $i -le $n/$a[0] -and $j -le $n/$a[1]) {
            [string[]]$result = ,($a[0]*$i),($a[1]*$j)
            Write-Host ($result -join ', ') " = " ($result | Measure-Object -Sum).Sum
        }
    }
}

This is .py script for Python:

import itertools

a = [420, 2500]
n = 16300

for i in range(1, n//a[0] + 1):
    for j in range(1, n//a[1] + 1):
        if i*a[0] + j*a[1] > 16200 and i*a[0] + j*a[1] < 16400 and i <= n//a[0] and j <= n//a[1]:
            print(sum(list(itertools.chain.from_iterable(itertools.repeat(x, y) for x, y in zip(a, [i, j])))))
