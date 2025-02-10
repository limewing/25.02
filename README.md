# 25.02

## 25.02.03
인터페이스를 사용하여 다른 클래스에서 해당 인터페이스를 구현하여 동일한 기능을 사용 - 코드의 재사용성 향상  
기본적으로 C#에서 클래스는 다중 상속을 지원하지 않지만 인터페이스는 지원함  
델리게이트는 매서드를 참조하는 일종의 함수 포인터  
람다를 사용하여 이름 없이 매서드를 만들 수 있음  
Func는 값을 반환하는 메서드를 나타내는 델리게이트  
Action은 값을 반환하지 않는 메서드를 나타내는 델리게이트  
LINQ는 .NET 프레임워크에서 제공되는 쿼리 언어 확장으로 데이터 소스에서 데이터를 쿼리하고 조작하는데 사용

## 25.02.05
일단 필요한 화면이 무엇인지 전부 분류한 다음에 거기에서 그 화면에 어떤 정보들이 담기는지 분류해두고 시작을 했어야 했는데 그러지 않았음  
static void 안에서 함수를 호출하려면 program 안에 있는 함수도 static으로 선언되어야 하기 때문에 불편함, 이를 우회하기 위해 class gamemanager를 만들고 그 안에 함수들을 만든 다음 gamemanager를 static 안에 만들어주고 그걸 통해서 함수를 호출함  
하위항목이 좀 많은 class는 따로 새 항목 만들기를 통해 만들어줌  
List<Item>을 인벤토리용과 상점용 두개를 따로 만들어주는게 관리에 훨씬 용이했을 듯 함  
MainScene if문 말고 switce case문이 더 깔끔해보임

## 25.02.06
public void TakeDamage(float Atk, float CritDmg, bool crit)      //  crit값은 확률의 판정여부를 계산하는 식의 리턴값을 집어넣음  
{
    float damage;  
    if (crit == true)  // 확률이 발동하여 적의 공격력에 적의 치명타 배율을 곱함  
    {  
        damage = Atk * CritDmg;  
        Console.Write("치명타! ");  
    }  
    else  
        damage = Atk;  // 확률이 발동하지 않아 치명타 배율을 곱하지 않음
    CurrentHealth -= (int)damage - Def - EquipDef;      //  현재 체력을 정수형으로 표현하고 싶어서 데미지값 소수 첫째자리 버림, 데미지를 반올림처리하는게 더 나을까 싶기도 함
    Console.Write($"{Name}이(가) {(int)damage - Def - EquipDef}의 데미지를 받았습니다.");  
    if (IsDead)  
        Console.WriteLine($"{Name}이(가) 죽었습니다.");  
    else  
        Console.WriteLine($"남은 체력: {CurrentHealth}");  
}  

## 25.02.10
class 안에 class 만들면 유지보수측면에서 불편해지니까 왠만하면 그렇게 하지 말자  
class를 만들었을때는 = new 생성자를 통해서 넣어줘야됨(객체로 만들어서 활용하기) 안하면 null Reference Exception  
class 안에 있는 데이터는 외부 반출 불가 - public 을 붙이면 다른 class에서도 활용 가능  
클래스는 기본이 internal  
  
class 왜 써야 하나요?  
  
객체지향(OOP)  
객체 사용으로 코드가 간결해짐 -> 코드 파악이 쉽다(가독성 증가)  
길어질 수 있는 코드를 나눠서 관리, 코드 관리에 좋음 -> 코드 분석 쉬움  
목적에 맞게 기능도 포함가능 -> 함수 사용  
정리  
-코드 파악이 쉽다  
-가독성 증가  
-유지보수 쉽다  
  
코드를 이해하기 쉽다  
