#include <bits/stdc++.h>

using namespace std;                            

int a[1005][1005];
bool visited[1005][1005];

int dx[4] = {-1, 0, 1, 0};
int dy[4] = {0, 1, 0, -1};

int dfs(int x, int y) {
    visited[x][y] = true;
    int kq = 1;
    int maxValue = -1;                                     // Gắn max = Gtri -1 , gắn nào cũng dc vì lập 4 lần nên mặc địh sẽ gắn bé nhất la -1
    int next_x = -1;
    int next_y = -1;
    for (int i = 0; i < 4; i++) {                                   // THực hiện ktra trên dưới trái phải và gắn vị trí tiếp theo
        int xKTra = x + dx[i];
        int yKTra = y + dy[i];
        if ( !visited[xKTra][yKTra] && a[xKTra][yKTra] > maxValue) {  // Nếu chưa đi và lớn hơn số ban đầu 
            maxValue = a[xKTra][yKTra];
            next_x = xKTra;
            next_y = yKTra;
        }
    }
    if (next_x != -1 && next_y != -1) {
        kq += dfs(next_x, next_y);
        
    }
    return kq;
}
