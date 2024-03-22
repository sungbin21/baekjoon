# baekjoon 
//백준 1주차 동전 문제입니다
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt(); // 동전의 종류 수
        int k = scanner.nextInt(); // 목표 금액

        int[] coins = new int[n]; // 동전의 가치를 저장할 배열
        for (int i = 0; i < n; i++) {
            coins[i] = scanner.nextInt();
        }

        // dp[i]는 금액 i를 만들 수 있는 경우의 수
        int[] dp = new int[k + 1];
        dp[0] = 1; // 금액이 0원일 때는 아무 동전도 사용하지 않는 경우 1가지

        for (int coin : coins) {
            for (int i = coin; i <= k; i++) {
                dp[i] += dp[i - coin];
            }
        }

        System.out.println(dp[k]);
    }
}
