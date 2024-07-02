import random


def guess_number_game():
    print("업다운 게임을 시작합니다!")
    play_again = 'y'
    best_attempt = float('inf')  # 이전 게임의 최고 시도 횟수를 저장할 변수

    while play_again.lower() == 'y':
        target_number = random.randint(1, 100)  # 1에서 100 사이의 랜덤한 숫자 선택
        attempts = 0
        print(f"이전 게임 플레이어 최고 시도 횟수: {best_attempt}")

        while True:
            try:
                user_input = int(input("숫자를 입력하세요: "))
                if user_input < 1 or user_input > 100:
                    print("유효한 범위 내의 숫자를 입력하세요.")
                    continue

                attempts += 1

                if user_input > target_number:
                    print("Down")
                elif user_input < target_number:
                    print("Up")
                else:
                    print("맞았습니다!")
                    print(f"시도한 횟수: {attempts}")

                    # 최고 시도 횟수 업데이트
                    if attempts < best_attempt:
                        best_attempt = attempts

                    break
            except ValueError:
                print("올바른 숫자를 입력하세요.")

        play_again = input("다시 하시겠습니까? (y/n): ")

    print("게임을 종료합니다.")



# 게임 실행
guess_number_game()
