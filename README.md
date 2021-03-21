# DataStructure-Queue


// Queue Implementation with Linked List

class Node<T> {
  var value:T
  var next:Node?
  init(value:T) {
    self.value = value
  }
}

class Queue<T> {
  var tail:Node<T>?
  var head:Node<T>?
  var count:Int = 0
    
  func dequeue () -> Node<T>? {
    if let node = head {
      head = head?.next
      count -= 1
      return node
    }
    return nil
  }
    
  func enqueue(value:T) {
    let newNode = Node(value:value)
    if let tailNode = tail {
      tailNode.next = newNode
      newNode.next = nil
      tail = newNode
    } else {
      head = newNode
      tail = newNode
    }
    count += 1
  }
}

let q = Queue<Any>()

q.enqueue(value: 5)
q.enqueue(value: 10)


print(q.count)


//Queue implementation using Array

struct QueueUsingArray<T>{
    
    
    var queueElement : [T] = []
    
    
    
    var isEmpty: Bool{
        return queueElement.isEmpty
    }
    
    var  peek: T?{
        
        queueElement.first
        
    }

    var description: String{
        
        if isEmpty{
                    
            return "Queue is Empty"
        }

        var queu = ""
        for i in queueElement{
            
            queu = queu+"=>\(i)"
        }

        return queu

    }
    
    mutating func deQueue()-> T{
        
        queueElement.remove(at: 0)
    }
    
    mutating func enQueue(value: T){
        
        queueElement.append(value)
    }

}


var queuUsing = QueueUsingArray<Any>()

queuUsing.enQueue(value: 5)
queuUsing.enQueue(value: 12)
queuUsing.enQueue(value: 15)
queuUsing.enQueue(value: 18)
queuUsing.enQueue(value: 2)
print(queuUsing.description)
queuUsing.deQueue()
print(queuUsing.description)




//Queues Implementation Using Stacks

struct QueueWithStacks<T>{
    
    var s1  = [T]()
    var s2 = [T]()
    
    mutating func enqueue(value: T){
        s1.append(value)
    }
    
    mutating func dequeu() -> T? {
        
        if s2.isEmpty{
            
            if s1.isEmpty{
                print("Queue is emplty")
                return nil
            }else{
                
                s2 = s1.reversed()
                s1.removeAll()
            }
        }
        return s2.removeLast()
    }
    
    mutating func peek()->T?{
        
        if s2.isEmpty{
            
            if s1.isEmpty{
              
                print("Queue is emplty")
                return nil
                
            }else{
                return s1.first
            }
        }else{

            return s2.last
       
        }
//        return nil
    }
}
var que = QueueWithStacks<Any>()
que.enqueue(value: 12)
que.enqueue(value: 13)
que.enqueue(value: 14)
que.enqueue(value: 15)
que.enqueue(value: 16)
que.enqueue(value: 17)
que.enqueue(value: 18)
que.enqueue(value: 19)
que.peek()
que.dequeu()
que.peek()
que.dequeu()
que.peek()


