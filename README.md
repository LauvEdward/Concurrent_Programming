# Concurrent Programming
Learn async/await, actors, async-let, task groups, unstructured concurrency, detached tasks and more!
## 1.Dispatch Queue:
### Main: 
Using run main thread and UI
### Global:
QoS: User interactive, User initiated, default, Utility, Background, Unpecified.<br />
Creating a serial queue:

    let queue = DispatchQueue(label: "Serial Queue")
    queue.async{
    // this task is executed first
    }
    queue.async {
    // this task is executed second
    }
Creating a concurrent queue:
    
    let queue = DispatchQueue(label: "Concurrent Queue", attributes: .concurrent)
    queue.async{
    }
    queue.async {
    }
Background queue:

    DispatchQueue.global().async {
    // download the image
    // refresh the UI
    }
>it's wrong, replace:

    DispatchQueue.global().async {
    // download the image
      DispathQueue.main.async {
        // refresh the UI
      }
    }
