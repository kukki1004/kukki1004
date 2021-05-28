#include <iostream>
#include <cmath>
#include <cstdlib>
#include <ctime>
#include <random>
#define N 10
#define MAX 5
#define SIZE 1000000

using namespace std;

int main()
{
    srand(time(NULL));

    int n = 1000;
    int stp = 100;

    int z1 = 2;
    int z2 = 79;
    int e = 1;
    int e1 = pow(10, 6);
    int e2 = 5 * e1;
    int e3 = pow(10, 7);

    int bmax, bmin;

    random_device rd;
    mt19937 gen(rd());
    normal_distribution<double> dist(0, 1);

    int count[N];
    for (int i = 0; i < SIZE; i++)
    {
        double b = fabs(dist(gen));
        if(b>MAX) count[MAX]++;
        else count[(int)(b / MAX * N)]++;
    }
    printf(" range_of_b  theta(rad)    count\n");
    for (int i = 0; i < N; i++){
        double y = 2 * atan(z1 * z2 * pow(e, 2) / (2 * ((double)i*MAX/N) * e1));
        printf("%.2f ~ %.2f  %.8f  %d\n", (double)i*MAX/N, (double)(i+1)*MAX/N, y, count[i]);
    }

    return 0;
}
