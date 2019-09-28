
### 문제 설명

체스에서 비숍(Bishop)은 아래 그림과 같이 대각선 방향으로 몇 칸이든 한 번에 이동할 수 있습니다. 만약, 한 번에 이동 가능한 칸에 체스 말이 놓여있다면 그 체스 말을 잡을 수 있습니다.

![bishop1.png](https://grepp-programmers.s3.amazonaws.com/files/ybm/07fd25eb65/561e9310-6ee3-4ecf-85bd-dd573bdbb8df.png)

8 x 8 크기의 체스판 위에 여러 개의 비숍(Bishop)이 놓여있습니다. 이때, 비숍(Bishop)들에게  **한 번에**  잡히지 않도록 새로운 말을 놓을 수 있는 빈칸의 개수를 구하려고 합니다.

위 그림에서 원이 그려진 칸은 비숍에게 한 번에 잡히는 칸들이며, 따라서 체스 말을 놓을 수 있는 빈칸 개수는 50개입니다.

8 x 8 체스판에 놓인 비숍의 위치 bishops가 매개변수로 주어질 때, 비숍에게 한 번에 잡히지 않도록 새로운 체스 말을 놓을 수 있는 빈칸 개수를 return 하도록 solution 함수를 완성해주세요.

#### 제한 조건

체스판에 놓인 비숍의 위치 bishops가 solution 함수의 매개변수로 주어집니다.

-   bishops는 비숍의 위치가 문자열 형태로 들어있는 배열입니다.
-   bishops의 길이는 1 이상 64 이하입니다.
-   비숍이 놓인 위치는 알파벳 대문자와 숫자로 표기합니다.
    -   알파벳 대문자는 가로 방향, 숫자는 세로 방향 좌표를 나타냅니다.
    -   예를 들어 위 그림에서 비숍이 있는 칸은  D5라고 표현합니다.
-   한 칸에 여러 비숍이 놓이거나, 잘못된 위치가 주어지는 경우는 없습니다.

#### 입출력 예

|bishops  | return |
|--|--|
|[D5]|50|
|[D5,  E8,  G2]|42|

#### 입출력 예 설명

입출력 예 #1  
문제에 나온 예시와 같습니다.

입출력 예 #2

![bishop2.png](https://grepp-programmers.s3.amazonaws.com/files/ybm/b635b0d993/71863e6c-1320-4ce1-8b5b-886c37dcfa5b.png)

그림과 같이 원이 그려진 칸은 비숍에게 한 번에 잡히는 칸들이며, 따라서 체스 말을 놓을 수 있는 빈칸 개수는 42개입니다.

### 나의 답
```java
import java.util.*;

class Solution {
    public int solution(String[] bishops) {
      int bx[] = {-1,1};
        int by[] = {-1,1};
        int chk[][] = new int[9][9];
        for(int k = 0 ; k < bishops.length;k++){
            int x = (int)(bishops[k].charAt(0))-64;
            
            int y = (int)(bishops[k].charAt(1))-48;

            while(x>1 && y >1){
                x+=bx[0];
                y+=by[0];
                chk[x][y]=1;
            }
            x = (int)(bishops[k].charAt(0))-64;
            y = (int)(bishops[k].charAt(1))-48;
            while(x>1 && y<8){
                x+=bx[0];
                y+=by[1];
                chk[x][y]=1;
            }
            x = (int)(bishops[k].charAt(0))-64;
            y = (int)(bishops[k].charAt(1))-48;
            while(x<8 && y >1){
                x+=bx[1];
                y+=by[0];
                chk[x][y]=1;
            }
             x = (int)(bishops[k].charAt(0))-64;
            y = (int)(bishops[k].charAt(1))-48;
            while(x<8 && y <8){
                x+=bx[1];
                y+=by[1];
                chk[x][y]=1;
            }
        }
        for(String bishop : bishops){
             int x = (int)(bishop.charAt(0))-64;          
            int y = (int)(bishop.charAt(1))-48;
            chk[x][y]=1;
        }
        int answer = 0;
            for(int i = 1; i <=8;i++){
                for(int j = 1 ;j <=8;j++){
                if(chk[i][j]==0) answer++;
            }
            }
        
        return answer;
    }
}
```
> Written with [StackEdit](https://stackedit.io/).
