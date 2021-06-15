### 利用递归的思想来解题

#### 硬币组合


```
private static int [] rewards = {1,2,5,10};
    private static int totalCount = 0;
    public static void main(String[] args) {
        get(10, new ArrayList<>());
        System.out.println(totalCount);
    }

    public static void get(int totalReward, ArrayList<Integer> result) {
        if (totalReward == 0) {
            totalCount++;
            System.out.println(result);
            return;
        }
        if (totalReward < 0) {
            return;
        } else {
            for (int i = 0; i < rewards.length; i++) {
                ArrayList<Integer> newResult = (ArrayList<Integer>)(result.clone());
                newResult.add(rewards[i]);
                get(totalReward - rewards[i], newResult);
            }
        }
    }
```

#### 整数拆解乘积
```
public static void get(int totalReward, ArrayList<Integer> result) {
        if (totalReward == 1) {
            if (result.size() == 1) {
                result.add(1);
            }
            System.out.println(result);
            return;
        } else {
            for (int i = 1; i <= totalReward; i++) {
                if (result.contains(1) && i == 1) {
                    continue;
                }
                ArrayList<Integer> newResult = (ArrayList<Integer>)(result.clone());
                newResult.add(i);
                if (totalReward % i != 0) {
                    continue;
                }
                get(totalReward/i, newResult);
            }
        }
    }
```

### 最少硬币组合
```
public static int getMinMoney(int[] c, int[] value) {
        int[] t = new int[3];
        for (int i = 0; i < c.length; i++) {
            for (int j = 0; j < value.length; j++) {
                if (i - value[j] >= 0) {
                    t[j] = c[i - value[j]] + 1;
                }
            }
            int min = Math.min(t[0], t[1]);
            min = Math.min(min, t[2]);
            c[i] = min;
        }
        return c[c.length - 1];
    }
```
