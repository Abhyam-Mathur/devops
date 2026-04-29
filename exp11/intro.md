# Experiment 11: Container Orchestration with Docker Stack

## Title
Orchestration using Docker Compose and Docker Swarm.

## Objective
Move from simple multi-container deployment to orchestration with scaling and self-healing.

## Theory
Orchestration is the automatic management of containers.

Compared with plain `docker run`, orchestration adds:
- Scaling
- Self-healing
- Load balancing
- Multi-host support

## Progression Path
```text
docker run -> Docker Compose -> Docker Swarm -> Kubernetes
```

## From Compose to Swarm
You already know Compose from Experiment 6. Swarm keeps the same Compose-style file but manages services rather than raw containers.

## Practical Steps
### 1. Clean up existing Compose setup
```bash
docker compose down -v
docker ps
```

### 2. Initialize Swarm
```bash
docker swarm init
docker node ls
```

### 3. Deploy a stack
```bash
docker stack deploy -c docker-compose.yml wpstack
```

### 4. Verify services
```bash
docker service ls
docker service ps wpstack_wordpress
docker ps
```

### 5. Access the app
```text
http://localhost:8080
```

### 6. Scale the app
```bash
docker service scale wpstack_wordpress=3
docker service ls
```

### 7. Test self-healing
```bash
docker ps | grep wordpress
docker kill <container-id>
docker service ps wpstack_wordpress
```

### 8. Remove the stack
```bash
docker stack rm wpstack
docker service ls
docker ps
```

## Key Observations
| Feature | Compose | Swarm |
|---|---|---|
| Scope | Single host | Multi-host cluster |
| Scaling | Basic | Built-in service scaling |
| Self-healing | No | Yes |
| Load balancing | No | Yes |

## Result
Docker Stack and Swarm provide orchestration features on top of the familiar Compose file format.
