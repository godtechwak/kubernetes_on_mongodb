# *MongoDB 레플리카셋 쿠버네티스 설치 방법*
### 1. ConfigMap 설치
```bash
kctl apply -f mongodb-configmap.yaml
```
### 2. Service 설치
```bash
kctl apply -f mongodb-service.yaml
```
### 3. Statefulset 설치
```bash
kctl apply -f mongodb-statefulset.yaml
```
# *MongoDB 레플리카셋 쿠버네티스 접속 방법*
### 1. mongos가 설치된 pod 터미널 접속
```bash
kubectl run mongodb-client --rm -it --image=mongo --command -- /bin/bash
```
### 2. mongo 접속
```bash
mongosh mongodb://mongodb-0.mongodb.mongodb.svc.cluster.local:27017
```
### 3. 레플리카셋 초기화
```bash
rs.initiate()
```
### 4. 레플리카셋 상태 확인
```bash
rs.status()
{
  set: 'rs0',
  date: ISODate('2024-10-24T08:53:18.226Z'),
  myState: 1,
  term: Long('1'),
  syncSourceHost: '',
  syncSourceId: -1,
  heartbeatIntervalMillis: Long('2000'),
  majorityVoteCount: 2,
  writeMajorityCount: 2,
  votingMembersCount: 3,
  writableVotingMembersCount: 3,
  optimes: {
    lastCommittedOpTime: { ts: Timestamp({ t: 1729759994, i: 1 }), t: Long('1') },
    lastCommittedWallTime: ISODate('2024-10-24T08:53:14.062Z'),
    readConcernMajorityOpTime: { ts: Timestamp({ t: 1729759994, i: 1 }), t: Long('1') },
    appliedOpTime: { ts: Timestamp({ t: 1729759994, i: 1 }), t: Long('1') },
    durableOpTime: { ts: Timestamp({ t: 1729759994, i: 1 }), t: Long('1') },
    writtenOpTime: { ts: Timestamp({ t: 1729759994, i: 1 }), t: Long('1') },
    lastAppliedWallTime: ISODate('2024-10-24T08:53:14.062Z'),
    lastDurableWallTime: ISODate('2024-10-24T08:53:14.062Z'),
    lastWrittenWallTime: ISODate('2024-10-24T08:53:14.062Z')
  },
  lastStableRecoveryTimestamp: Timestamp({ t: 1729759962, i: 1 }),
  electionCandidateMetrics: {
    lastElectionReason: 'electionTimeout',
    lastElectionDate: ISODate('2024-10-24T08:52:53.994Z'),
    electionTerm: Long('1'),
    lastCommittedOpTimeAtElection: { ts: Timestamp({ t: 1729759962, i: 1 }), t: Long('-1') },
    lastSeenWrittenOpTimeAtElection: { ts: Timestamp({ t: 1729759962, i: 1 }), t: Long('-1') },
    lastSeenOpTimeAtElection: { ts: Timestamp({ t: 1729759962, i: 1 }), t: Long('-1') },
    numVotesNeeded: 2,
    priorityAtElection: 1,
    electionTimeoutMillis: Long('10000'),
    numCatchUpOps: Long('0'),
    newTermStartDate: ISODate('2024-10-24T08:52:54.047Z'),
    wMajorityWriteAvailabilityDate: ISODate('2024-10-24T08:52:54.533Z')
  },
  members: [
    {
      _id: 0,
      name: 'mongodb-0.mongodb:27017',
      health: 1,
      state: 1,
      stateStr: 'PRIMARY',
      uptime: 167,
      optime: { ts: Timestamp({ t: 1729759994, i: 1 }), t: Long('1') },
      optimeDate: ISODate('2024-10-24T08:53:14.000Z'),
      optimeWritten: { ts: Timestamp({ t: 1729759994, i: 1 }), t: Long('1') },
      optimeWrittenDate: ISODate('2024-10-24T08:53:14.000Z'),
      lastAppliedWallTime: ISODate('2024-10-24T08:53:14.062Z'),
      lastDurableWallTime: ISODate('2024-10-24T08:53:14.062Z'),
      lastWrittenWallTime: ISODate('2024-10-24T08:53:14.062Z'),
      syncSourceHost: '',
      syncSourceId: -1,
      infoMessage: 'Could not find member to sync from',
      electionTime: Timestamp({ t: 1729759974, i: 1 }),
      electionDate: ISODate('2024-10-24T08:52:54.000Z'),
      configVersion: 1,
      configTerm: 1,
      self: true,
      lastHeartbeatMessage: ''
    },
    {
      _id: 1,
      name: 'mongodb-1.mongodb:27017',
      health: 1,
      state: 2,
      stateStr: 'SECONDARY',
      uptime: 35,
      optime: { ts: Timestamp({ t: 1729759994, i: 1 }), t: Long('1') },
      optimeDurable: { ts: Timestamp({ t: 1729759994, i: 1 }), t: Long('1') },
      optimeWritten: { ts: Timestamp({ t: 1729759994, i: 1 }), t: Long('1') },
      optimeDate: ISODate('2024-10-24T08:53:14.000Z'),
      optimeDurableDate: ISODate('2024-10-24T08:53:14.000Z'),
      optimeWrittenDate: ISODate('2024-10-24T08:53:14.000Z'),
      lastAppliedWallTime: ISODate('2024-10-24T08:53:14.062Z'),
      lastDurableWallTime: ISODate('2024-10-24T08:53:14.062Z'),
      lastWrittenWallTime: ISODate('2024-10-24T08:53:14.062Z'),
      lastHeartbeat: ISODate('2024-10-24T08:53:18.031Z'),
      lastHeartbeatRecv: ISODate('2024-10-24T08:53:17.041Z'),
      pingMs: Long('0'),
      lastHeartbeatMessage: '',
      syncSourceHost: 'mongodb-0.mongodb:27017',
      syncSourceId: 0,
      infoMessage: '',
      configVersion: 1,
      configTerm: 1
    },
    {
      _id: 2,
      name: 'mongodb-2.mongodb:27017',
      health: 1,
      state: 2,
      stateStr: 'SECONDARY',
      uptime: 35,
      optime: { ts: Timestamp({ t: 1729759994, i: 1 }), t: Long('1') },
      optimeDurable: { ts: Timestamp({ t: 1729759994, i: 1 }), t: Long('1') },
      optimeWritten: { ts: Timestamp({ t: 1729759994, i: 1 }), t: Long('1') },
      optimeDate: ISODate('2024-10-24T08:53:14.000Z'),
      optimeDurableDate: ISODate('2024-10-24T08:53:14.000Z'),
      optimeWrittenDate: ISODate('2024-10-24T08:53:14.000Z'),
      lastAppliedWallTime: ISODate('2024-10-24T08:53:14.062Z'),
      lastDurableWallTime: ISODate('2024-10-24T08:53:14.062Z'),
      lastWrittenWallTime: ISODate('2024-10-24T08:53:14.062Z'),
      lastHeartbeat: ISODate('2024-10-24T08:53:18.032Z'),
      lastHeartbeatRecv: ISODate('2024-10-24T08:53:17.040Z'),
      pingMs: Long('0'),
      lastHeartbeatMessage: '',
      syncSourceHost: 'mongodb-0.mongodb:27017',
      syncSourceId: 0,
      infoMessage: '',
      configVersion: 1,
      configTerm: 1
    }
  ],
  ok: 1,
  '$clusterTime': {
    clusterTime: Timestamp({ t: 1729759994, i: 1 }),
    signature: {
      hash: Binary.createFromBase64('AAAAAAAAAAAAAAAAAAAAAAAAAAA=', 0),
      keyId: Long('0')
    }
  },
  operationTime: Timestamp({ t: 1729759994, i: 1 })
}
```
### 5. admin 유저 생성
```bash
$ use admin
$ db.createUser({user:'admin', pwd:'admin', roles:[{role:'root', db:'admin'}]})
```
### 6. admin 유저로 접속
```bash
$ mongosh -u admin --host 'mongodb-0.mongodb.mongodb.svc.cluster.local:27017'
또는
$ mongosh 'mongodb://admin:admin@mongodb-0.mongodb.mongodb.svc.cluster.local:27017'
```

