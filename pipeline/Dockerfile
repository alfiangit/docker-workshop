FROM python:3.13.11-slim
# copy from another docker image
COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin/
WORKDIR /code
# when you specify things below,
# when doing ENTRY you can delete "uv" and "run" from 
# ENTRYPOINT ["uv", "run", "python", "pipeline.py"]
ENV PATH="/code/.venv/bin:$PATH"
# you do this. so what's in docker, will be the same as in local.
# before this stage, please specify current directory
COPY pyproject.toml .python-version uv.lock ./
# basically installing packages / dependencies based uv.lock. 
# 100% exactly the same as local.
# make sure in local you do this when creating venv using uv
# uv init --python 3.13 --no-package
# if you not stating --no-package, leads to error because earlier configuration.
RUN uv sync --locked
COPY pipeline.py .
# no need "uv" and "run" because you set ENV path!
ENTRYPOINT ["python", "pipeline.py"]

# #1 DEFAULT
# FROM python:3.13.11-slim
# RUN pip install pandas pyarrow
# WORKDIR /code
# COPY pipeline.py .

# I THINK WE DON'T WANT TO MANUALLY RUN THE FILE IN THE DOCKER
# RERUN THE docker run -t test:pandas
# IF YOU PREVIOUSLY RUN, SEVERAL LAYER IS ALREADY CACHED SO IT WILL BE FASTER
# DON't FORGET TO PUT ARGUMENT

# #2 
# FROM python:3.13.11-slim
# RUN pip install pandas pyarrow
# WORKDIR /code
# COPY pipeline.py .
# ENTRYPOINT ["python", "pipeline.py"]

# #3
# # WHEN USING UV
# FROM python:3.13.11-slim
# # copy from another docker image
# COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin/
# WORKDIR /code
# # you do this. so what's in docker, will be the same as in local.
# # before this stage, please specify current directory
# COPY pyproject.toml .python-version uv.lock ./
# # basically installing packages / dependencies based uv.lock. 
# # 100% exactly the same as local.
# # make sure in local you do this when creating venv using uv
# # uv init --python 3.13 --no-package
# # if you not stating --no-package, leads to error because earlier configuration.
# RUN uv sync --locked
# COPY pipeline.py .
# ENTRYPOINT ["uv", "run", "python", "pipeline.py"]

# #4
# WITHOUT "UV" AND "RUN" ARGUMENT
# FROM python:3.13.11-slim
# # copy from another docker image
# COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin/
# WORKDIR /code
# # when you specify things below,
# # when doing ENTRY you can delete "uv" and "run" from 
# # ENTRYPOINT ["uv", "run", "python", "pipeline.py"]
# ENV PATH="/code/.venv/bin:$PATH"
# # you do this. so what's in docker, will be the same as in local.
# # before this stage, please specify current directory
# COPY pyproject.toml .python-version uv.lock ./
# # basically installing packages / dependencies based uv.lock. 
# # 100% exactly the same as local.
# # make sure in local you do this when creating venv using uv
# # uv init --python 3.13 --no-package
# # if you not stating --no-package, leads to error because earlier configuration.
# RUN uv sync --locked
# COPY pipeline.py .
# # no need "uv" and "run" because you set ENV path!
# ENTRYPOINT ["python", "pipeline.py"]