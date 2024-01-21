### Chain

- public getBlocks

    - 보안상으로 엄청난 문제 

- 누구든지, 여기 있는 여러 단계를 거치지 않고도, 블록체인에 새로운 블록을 추가할 수 있다는 것 

- this.blocks를 리턴하는데..
    
    - 그 값은 private인데?

- 리턴해주는 대신에, 새로운 배열을 리턴해주자 

```typescript
public getBlocks() {
        return [...this.blocks];
}
```
