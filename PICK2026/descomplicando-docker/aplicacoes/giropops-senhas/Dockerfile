FROM cgr.dev/chainguard/python:latest-dev as dev

WORKDIR /app

RUN python -m venv venv
ENV PATH="/app/venv/bin":$PATH
COPY giropops-senhas/requirements.txt requirements.txt
RUN pip install -r requirements.txt

FROM cgr.dev/chainguard/python:latest

WORKDIR /app

COPY --from=dev /app /app
ENV PATH="/app/venv/bin:$PATH"

COPY giropops-senhas/requirements.txt .
COPY giropops-senhas/app.py .
COPY giropops-senhas/templates templates/
COPY giropops-senhas/static static/

EXPOSE 5000

CMD ["flask", "run", "--host=0.0.0.0"]

