---
layout: post
title: "스택 (Stack)"
ref: ds-stack
date: 2018-11-27 17:22:00
last_modified_at: 2020-01-25 16:28:00
categories: 
 - Data Structure
lang: ko
---

## 목차
- [스택(Stack) 이란?](#concept)
- [연산](#op)
- [구현](#implement)
  + [연결 리스트(Linked List) 기반](#linkedlist)
  + [배열(Array) 기반](#array)
- [사용 사례](#app)
- [풀어볼 문제](#try)

<div class="divider"></div>
## 스택(Stack) 이란? <a id="concept"></a>
스택은 선형 자료구조의 일종으로 **LIFO** (Last-In First-Out) 또는 **FILO** (First-In Last-out) 
디자인을 따르며, 구조의 특성 상 자료의 추가와 제거는 스택의 끝에서 이루어진다.

<div class="divider"></div>
## 연산 <a id="op"></a>
 - **push**: 스택에 데이터를 추가한다
 - **pop**: 스택에서 최근 항목을 삭제한다
 - **top**: 스택의 끝(최근 항목)을 반환한다
 - **isEmpty**: 스택이 비어있는지 확인한다
 - **getSize**: 스택에 들어 있는 항목의 총 개수를 반환한다

<div class="divider"></div>
## 구현 <a id="implement"></a>
 스택은 연결 리스트와 배열로 구현할 수 있으며, 각각의 장단점이 존재한다.

 **연결 리스트**로 구현할 경우
 - 데이터 추가/제거 비용:  O(1)
 - 데이터 접근 비용: O(n)

 **배열**로 구현할 경우, 
 - 데이터 추가 비용: O(1)
 - 데이터 제거 비용: O(n) 
 - 데이터 접근 비용: O(1)

데이터 추가와 제거 연산의 비용이 접근 연산보다 훨씬 큰 경우 연결 리스트를 사용하고,
보다 작을 때는 배열을 쓰는 편이 좋다.
 
<div class="divider"></div>
### 연결 리스트(Linked List) 기반 <a id="linkedlist"></a>

```java
public class Stack
{
    private Node head;
    private int length;

    // Constructor
    public Stack()
    {
        head = null;
    }

    // inserts an item to the stack
    public void push(int data)
    {
        Node node = new Node(data);
        node.next = head;
        head = node;

        ++length;
    }

    // removes last item from the stack
    public int pop()
    {
        if (isEmpty())
        {
            System.out.println("Stack Underflow..");
            System.exit(1);
        }

        int item = head.data;
        head = head.next;
        --length;

        return item;
    }

    public Integer top()
    {
        if (head == null)
        {
            System.out.println("Stack is empty");
            return null;
        }

        return head.data;
    }

    public boolean isEmpty()
    {
        return head == null;
    }

    public Integer getSize()
    {
        return length;
    }

    // Helper Class
    class Node
    {
        private int data;
        private Node next;

        public Node(int item)
        {
            data = item;
            next = null;
        }
    }
}
```

<div class="divider"></div>
### 배열(Array) 기반 <a id="array"></a>

```java
public class Stack {
    private Integer[] stack;
    private int size;       // maximum size of the stack
    private int top;        // current position on the stack

    // Constructor
    public Stack(int size)
    {
        stack = new Integer[size];
        this.size = size;
        top = -1;
    }

    // inserts an item to the stack
    public void push(int item)
    {
        if (isFull())
        {
            System.out.println("Stack Overflow..");
            System.exit(1);
        }

        stack[++top] = item;
    }

    // removes last item from the stack
    public int pop()
    {
        if (isEmpty())
        {
            System.out.println("Stack Underflow..");
            System.exit(1);
        }

        int item = stack[top--];
        return item;
    }

    // print data on top of the stack
    public Integer top()
    {
        if (top == 0)
        {
            System.out.println("Stack is empty..");
            return null;
        }

        return stack[top];
    }

    public boolean isEmpty()
    {
        return top == -1;
    }

    public int getSize()
    {
        return size;
    }


    public boolean isFull()
    {
        return top == size;
    }
}
```

<div class="divider"></div>
## 사용 사례 <a id="app"></a>
- 퇴각 검색/되추적 (Backtracking) 알고리즘
- 편집기 - Redo & Undo
- 그래프 알고리즘
- 트리 순회(Traversal) 알고리즘
- 웹 브라우저
- 수식 문제

<div class="divider"></div>
## 풀어볼 문제 <a id="try"></a>
From. @[acmicpc.net](https://www.acmicpc.net)

- [1918. 후위 표기식](https://www.acmicpc.net/problem/1918)
- [5397. 키로거](https://www.acmicpc.net/problem/5397)
- [9012. 괄호](https://www.acmicpc.net/problem/9012)
- [10828. 스택](https://www.acmicpc.net/problem/10828)