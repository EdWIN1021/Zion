# type assertions

Owner: Edwin

- Sometimes you will have information about the type of a value that TypeScript can’t know about
    
    ```tsx
    const myCanvas = document.getElementById("main_canvas") as HTMLCanvasElement;
    
    const myCanvas = <HTMLCanvasElement>document.getElementById("main_canvas");
    
    ```