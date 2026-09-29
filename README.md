#include <stdio.h>

int main(void) {
    int year = 0;
    int month = 0;
    int isLeap = 0;
    int days = 0;
    int weeks = 0;
    int rest = 0;

    printf("=== 습관 트래커 ===\n");

    // TODO 1-a: 연도 입력 및 범위 검증 (2000 ~ 2100)
    printf("연도를 입력하세요 (2000~2100): ");
    if (scanf("%d", &year) != 1) {
        return 0;
    }

    if (year < 2000 || year > 2100) {
        printf("[오류] 연도는 2000~2100 사이여야 합니다.\n");
        printf("프로그램을 종료합니다.\n");
        return 0;
    }

    // TODO 1-b: 월 입력 및 범위 검증 (1 ~ 12)
    printf("월을 입력하세요 (1~12): ");
    if (scanf("%d", &month) != 1) {
        return 0;
    }

    if (month < 1 || month > 12) {
        printf("[오류] 월은 1~12 사이여야 합니다.\n");
        printf("프로그램을 종료합니다.\n");
        return 0;
    }

    // TODO 2: 윤년 판정 (isLeap: 윤년이면 1, 아니면 0)
    // 4의 배수이면서 100의 배수가 아니거나, 400의 배수인 경우
    if ((year % 4 == 0 && year % 100 != 0) || (year % 400 == 0)) {
        isLeap = 1;
    } else {
        isLeap = 0;
    }

    // TODO 3-a: 그 달의 일수 구하기 (days)
    if (month == 2) {
        if (isLeap == 1) {
            days = 29;
        } else {
            days = 28;
        }
    } else if (month == 4 || month == 6 || month == 9 || month == 11) {
        days = 30;
    } else {
        days = 31;
    }

    // TODO 3-b: 일수를 7일씩 묶어 주 수와 남은 일수 구하기 (weeks, rest)
    weeks = days / 7;
    rest = days % 7;

    // [수정 금지] 결과 출력
    printf("\n[%d년 %d월]\n", year, month);
    
    if (isLeap) {
        printf("%d년은 윤년입니다.\n", year);
    } else {
        printf("%d년은 윤년이 아닙니다.\n", year);
    }

    printf("이 달은 %d일까지 있습니다.\n", days);
    printf("%d일 = %d주 %d일입니다.\n", days, weeks, rest);

    return 0;
}
