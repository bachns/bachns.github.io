---
layout: post
title: Mẫu Strategy C++
subtitle: Tách rời một chức năng ra khỏi đối tượng
tags: [Design Pattern, Strategy Pattern, C++]
categories: [Design Pattern]
---

Mẫu Strategy (mẫu chiến lược) là bạn tách rời phần xử lý một chức năng cụ thể ra khỏi đối tượng của bạn. Sau đó tạo ra một tập hợp các thuật toán để xử lý chức năng đó và lựa chọn thuật toán nào mà bạn thấy đúng đắn nhất khi thực thi chương trình. Strategy sử dụng khi có những tình huống sau:

* Bạn có một đoạn mã dễ thay đổi, và bạn tách chúng ra khỏi chương trình chính để dễ dàng bảo trì.
* Bạn muốn tránh sự rắc rối, khi phải hiện thực một chức năng nào đó qua quá nhiều lớp con.
* Bạn muốn thay đổi thuật toán sử dụng khi chạy chương trình.

**Ví dụ:** Chúng ta có nhiều loại phương tiện di chuyển StreetRacer, Helicopter, Jet... Mỗi loại trong số chúng lại có một cách di chuyển khác nhau. Hay nói cách khác, mỗi class lại có cách triển khai phương thức go() khác nhau. Do vậy ta sẽ tách phương thức go() này ra, và tạo một họ các cách triển khai cho nó. Khi đó, một lớp nào đó cần go() như thế nào ta sẽ set đúng nó.

![Strategy Pattern](/img/2020_04_27/strategy-pattern.png?raw=true){: .center-block :}

```cpp
#include <iostream>

//Interface
class GoAlgorithm
{
public:
	virtual void execGoAlgorithm() = 0;
	virtual ~GoAlgorithm() = default;
};

class GoByDriving : public GoAlgorithm
{
public:
	void execGoAlgorithm() override
	{
		std::cout << "Now I'm driving" << std::endl;
	}
};

class GoByFlying : public GoAlgorithm
{
public:
	void execGoAlgorithm() override
	{
		std::cout << "Now I'm flying" << std::endl;
	}
};

class GoByFlyingFast : public GoAlgorithm
{
public:
	void execGoAlgorithm() override
	{
		std::cout << "Now I'm flying fast" << std::endl;
	}
};

//Abstract class
class Vehicle
{
public:
	virtual ~Vehicle() = default;
	virtual void go()
	{
		mGoAlgorithm->execGoAlgorithm();
	}
	
	void setGoAlgorithm(GoAlgorithm* goAlgorithm)
	{
		mGoAlgorithm = goAlgorithm;
	}
private:
	GoAlgorithm* mGoAlgorithm = nullptr;
};

class StreetRacer : public Vehicle
{
public:
	StreetRacer()
	{
		setGoAlgorithm(new GoByDriving);
	}
};

class FormulaOne : public Vehicle
{
public:
	FormulaOne()
	{
		setGoAlgorithm(new GoByDriving);
	}
};

class Helicopter : public Vehicle
{
public:
	Helicopter()
	{
		setGoAlgorithm(new GoByFlying);
	}
};

class Jet : public Vehicle
{
public:
	Jet()
	{
		setGoAlgorithm(new GoByFlyingFast);
	}
};

int main(int argc, char* argv[])
{
	Vehicle* vehicle = new StreetRacer;
	vehicle->go();
	
	vehicle = new FormulaOne;
	vehicle->go();
	
	vehicle = new Helicopter;
	vehicle->go();
	
	std::cout << std::endl;
	vehicle = new Jet;
	vehicle->go();
	vehicle->setGoAlgorithm(new GoByDriving);
	vehicle->go();
	
	delete vehicle;
	return 0;
}
```

Kết quả nhận được:

```console
Now I'm driving
Now I'm driving
Now I'm flying

Now I'm flying fast
Now I'm driving
```

Wow, như vậy chúng ta có thể linh động cài đặt thuật toán phù hợp cho từng class. Và đặc biệt là có thể thay đổi được nó cả khi (runtime) chương trình đang chạy.