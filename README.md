# day25
N = int(input())  # 퇴사 전 남은 일 수
consultations = [tuple(map(int, input().split())) for _ in range(N)]

# dp[i]는 i일째부터 시작할 때 얻을 수 있는 최대 이익
dp = [0] * (N + 2)  # dp[N+1]까지 계산하므로 N+2 크기

# 뒤에서부터 dp 계산
for i in range(N - 1, -1, -1):
    Ti, Pi = consultations[i]
    # 상담을 했을 때 퇴사일 전이라면
    if i + Ti <= N:
        dp[i] = max(dp[i + 1], Pi + dp[i + Ti])
    else:
        dp[i] = dp[i + 1]

# dp[0]은 1일째부터 시작할 때 얻을 수 있는 최대 이익
print(dp[0])
