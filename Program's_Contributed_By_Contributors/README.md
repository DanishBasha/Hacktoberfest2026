Thank you for this repo :)
Please contribute any program here.


// SUDOKU SOLVER //

class Solution {
public:
    bool issafe(vector<vector<char>> &bd, int i, int j, char ch)
{
    for (int k = 0; k < 9; k++)
    {
        if (bd[k][j] == ch)
            return 0;
    }
    for (int k = 0; k < 9; k++)
    {
        if (bd[i][k] == ch)
            return 0;
    }

    int r = i - i % 3;
    int c = j - j % 3;
    for (int x = 0; x < 3; x++)
    {
        for (int y = 0; y < 3; y++)
        {
            if (bd[r + x][c + y] == ch)
                return 0;
        }
    }

    return 1;
}

bool sl(vector<vector<char>> &bd, int i, int j)
{
    if (i == 9)
        return 1;
    if (j == 9)
    {
        return sl(bd, i + 1, 0);
    }
    if (bd[i][j] != '.')
    {
        return sl(bd, i, j + 1);
    }

    for (char ch = '1'; ch <= '9'; ch++)
    {
        if (issafe(bd, i, j, ch))
        {
            bd[i][j] = ch;
            if (sl(bd, i, j + 1))
                return 1;
            bd[i][j] = '.';
        }
    }
    return 0;
}

void solveSudoku(vector<vector<char>> &bd)
{
    sl(bd, 0, 0);
}
};


// BINARY SEARCH IN PYTHON //

```python
def binary_search(arr: list[int], target: int) -> int:
    left = 0
    right = len(arr) - 1

    while left <= right:
        mid = (left + right) // 2

        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1

    return -1


if __name__ == "__main__":
    numbers = [2, 5, 8, 12, 16, 23, 38, 56, 72, 91]
    target_value = 23
    result = binary_search(numbers, target_value)
    print(f"Index: {result}")
```

