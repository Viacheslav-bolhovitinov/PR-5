#include <stdio.h>

#define MOD 12345

int main() {
    int n;
    printf("Введіть довжину послідовностей n (1 < n < 10000): ");
    scanf("%d", &n);

    if (n <= 1 || n >= 10000) {
        printf("Число не відповідає заданому діапазону.\n");
        return 1;
    }

    int dp0[n+1]; 
    int dp1[n+1]; 
    int dp2[n+1]; 

    dp0[1] = 1;
    dp1[1] = 1;
    dp2[1] = 0;

    for (int i = 2; i <= n; i++) {
        dp0[i] = (dp0[i-1] + dp1[i-1] + dp2[i-1]) % MOD;
        dp1[i] = dp0[i-1];
        dp2[i] = dp1[i-1];
    }

    int result = (dp0[n] + dp1[n] + dp2[n]) % MOD;

    printf("Кількість шуканих послідовностей: %d\n", result);

    return 0;
}
