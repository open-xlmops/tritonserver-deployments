# Triton Inference Server Deployments with Docker

## Tutorial

```Shell
./examples/fetch_models.sh

docker-compose up -d
docker-compose logs -f server
# All the models should show "READY" status to indicate that they loaded correctly.
# If a model fails to load the status will report the failure and a reason for the failure.
# If your model is not displayed in the table check the path to the model repository and your CUDA drivers.

# verify the tritonserver is running correctly
curl -v localhost:8000/v2/health/ready

docker-compose exec -it client bash
# execute the following command in container
$ /workspace/install/bin/image_client -m densenet_onnx -c 3 -s INCEPTION /workspace/images/mug.jpg
Request 0, batch size 1
Image '/workspace/images/mug.jpg':
    15.346230 (504) = COFFEE MUG
    13.224326 (968) = CUP
    10.422965 (505) = COFFEEPOT
```

## References

1. [Triton Inference Server - Get Started](https://github.com/triton-inference-server/server/blob/main/docs/getting_started/quickstart.md#launch-triton)