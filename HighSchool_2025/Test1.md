# �e�X�g 7/29�@

## ���̎�荞�݂���
VisualStuido���J���āA�R���\�[���A�v���@(C++,windows,�R���\�[���j�̃v���W�F�N�g�ŁA<br>
�v���W�F�N�g���������̖��O�ɂ��č쐬���Ă�������.�B
![Logo](https://enable01010.github.io/MyWeb/VS_HowCreate.png)

�����������ꂽ�v���O���������ׂč폜���āA���L�̃v���O������\��t���Ă��������B
~~~ clike
#include <iostream>
#include <string>
using namespace std;

int main()
{
    Question1();
    // Question2();
    // Question3();
    // Question4();
    // Question5();
    // Question6();
    // Question7();
    // Question8();
    // Question9();
    // Question10();

}

void Question1()
{
    // 3*5�̌v�Z���v���O�����ōs���o�͂��Ă��������B
}

void Question2()
{
    // ���̕\���X�y�[�X��؂�ŏo�͂��Ă��������B
}

void Question3()
{
    // 1000000�ȉ��̑f�����v�Z�ɂ���ċ��߂��ׂďo�͂��Ă��������B
}

void Question4()
{
    // 1����͂̎󂯎����s���A
    // ���̎󂯎�茋�ʂɁA"test"�Ɗ܂܂�Ă�����"Yes"�A�܂܂�Ă��Ȃ�������"No"�Əo�͂��Ă��������B
}

void Question5()
{
    // 2�񐔒l�̓��͎󂯎����s���A
    // ���̓�̐����̎l�����Z�̌��ʂ��X�y�[�X��؂�ŏo�͂��Ă��������B�B�i���Ԃ�+-*/�j
}

void Question6()
{
    // 1�񐔒l�̓��͎󂯎����s���A
    // ���̐��������̏ꍇ�h�����h�A��̏ꍇ"�"�Əo�͂��Ă��������B
}

void Question7()
{
    // 10�񐔒l�̓��͎󂯎����s���A
    // ���̒��ōł��傫�������o�͂��Ă��������B
}

void Question8()
{
    // 10�񐔒l�̓��͎󂯎����s���A
    // ���������������ɂ��āA�X�y�[�X��؂�ŕ\�����Ă��������B
}

void Question9()
{
    // �P��̓��͎󂯎����s���A
    // ���̓��͂̓��e���������ꍇ��"Yes"�A�Ԉ���Ă���ꍇ��"No"�ƕ\�����Ă��������B
    // ���͉͂��L�̂悤�Ȏl�����Z�̎��ł��B
    // 4 * 5 = 20
    // ���͕K���A�Z * �Z���Z�̂悤�ȓ�̐����̌v�Z���ʂ����߂���̂ł��B
}

void Question10()
{
    // 10��̓��͎󂯎����s���A�L�����N�^�[�̍��W��x, y����o�͂��Ă��������B
    // ���͂�WASD�̂����ꂩ�P�����ł��B
    // �EW�L�[�̏ꍇY���W���P�v���X
    // �EA�L�[�̏ꍇ�͂w���W���P�}�C�i�X
    // �E�r�L�[�̏ꍇ�͂x���W���P�}�C�i�X
    // �E�c�L�[�̏ꍇ�͂w���W���P�v���X
    // �L�����N�^�[�̏������W��x = 0, y = 0�ł��B
}

~~~

## ���̉�����
int main(�j�̒��Ɋ֐����p�ӂ��Ă���܂��B<br>
���̊֐��̒��g���������Ă��������B<br>
��F���1�������ꍇ�i�����͊Ԉ���Ă��܂��B�j<br>

~~~ clike
#include <iostream>
#include <string>
using namespace std;

int main()
{
    Question1();
    // Question2();
    // Question3();
    // Question4();
    // Question5();
    // Question6();
    // Question7();
    // Question8();
    // Question9();
    // Question10();

}

void Question1()
{
    // 3*5�̌v�Z���v���O�����ōs���o�͂��Ă��������B
    int number = 5;
    int number = 3;
    int answer = number * number;
    printf("%d",number);
}
~~~

## ���̐؂�ւ���
int main()�̒��ɂ���֐��̃R�����g�A�E�g�����ւ��鎖�ŕ\������������肩���鎖���ł��܂��B<br>
��F���2�������ꍇ
~~~ clike
#include <iostream>
#include <string>
using namespace std;

int main()
{
    // Question1();
    Question2();
    // Question3();
    // Question4();
    // Question5();
    // Question6();
    // Question7();
    // Question8();
    // Question9();
    // Question10();

}
~~~